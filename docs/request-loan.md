---
id: request-loan
title: Request loan
sidebar_label: Request loan
---

Loans can be requested by the borrower (self-signed) or using a creator, after the creation of the request, the above is available to be filled by a lender.

The entry point for requesting loans is the LoanManager; this contract handles the verification of the intent of the borrower/creator/cosigner. So all requests are performed calling such contract.

## Create a request

The requester can choose any conditions for the loan; bad conditions probably result in the request never being filled, avoiding this requires to set request parameters in line with the lenders market.

### Amount & Oracle

The Oracle defines what is going to be the currency of the loan, how many decimals that currency has, and how much is the equivalency of that currency to RCN; so the chosen Oracle will define the value of the requested amount.

~~~ javascript
// Oracle
// Currency: ARS
// Decimals: 2
const oracle = 0x22222c1944EfCC38CA46489f96c3A372C4dB74E6
// Requested amount, 100 ARS
const amount = 10000;
~~~

If the Oracle is set to 0x0, the currency is assumed to be RCN and the decimals of RCN are 18.

~~~ javascript
// No Oracle
// Currency: RCN
// Decimals: 18
const oracle = 0x0;
// Requested amount, 10 RCN
const amount = 10000000000000000000;
~~~

### Borrower

The borrower is the Ethereum address that is going to receive the tokens of the lend, this field can set to any address, but if the borrower is not the requester, the loan is considered not-approved and must be approved before filled. See [ApproBation](#Approbation).

### Expiration

Expiration is an absolute Unix-timestamp on which a non-filled request will no longer be valid; we recommend setting this parameter with a max value of 1 or 2 months from now.

### Model

The model is the brain of the loan, defines the repayments and interest scheme.

Each model defines its constructor, parameters, internal logic or even extensions, for this example, we are going to be using the InstallmentsModel reference model, but the process is similar for any model.

### Loan data

The loan data is an arbitrary length bytes parameter, acting as the creation data for the registry inside the [Model](#Model)

The model should provide a helper function to construct this loan data; here we are using the reference InstallmentsModel *encodeData* method.

~~~ solidity
    function encodeData(
        uint128 _cuota,
        uint256 _interestRate,
        uint24 _installments,
        uint40 _duration,
        uint32 _timeUnit
    ) external pure returns (bytes) {
        return abi.encodePacked(
            _cuota,
            _interestRate,
            _installments,
            _duration,
            _timeUnit
        );
    }
~~~
> Note: In this case the encoded data is just packed using abi.encodePacked, this is a common pattern but is not part of the protocol

#### Installments model data properties

| Parameter     | Type    | Description                                                                   |
|---------------|---------|-------------------------------------------------------------------------------|
| _cuota        | uint128 | Amount to pay in each installment                                             |
| _interestRate | uint256 | Interest rate by second, encoded as the denominator of 10 000 000             |
| _installments | uint24  | Total number of installments                                                  |
| _duration     | uint40  | Duration of each installment                                                  |
| _timeUnit     | uint32  | Min time-frame of the loan, time deltas lower than this value will be ignored |

## Approbation

> Note: This process is not required for self-signed loans.

Loans created by a creator being their lifecycle as non-approved, those loans are not available to be filled and require an additional step establishing the borrower approve.

This verification can be performed in different ways:

### Direct approve

A direct approve is the simplest way to approve a request; the borrower should call the approveRequest method, any Ethereum address or contract can call this method.

~~~ solidity
bool success = loanManager..approveRequest(_id);
~~~

If the approve is successful, the call returns true and emit an Approved(_id) event.