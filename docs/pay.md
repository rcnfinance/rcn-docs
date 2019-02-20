---
id: pay
title: Pay loan 
sidebar_label: Pay loan 
---

The point of entry to pay a loan is the Debt Engine. This contract allows any address to pay the debt of a borrower, totally or partially.

The sender address of the payment transaction should have enough funds to pay for the amount entered.

## Pay function

~~~ javascript
// Pay function interface

function pay(
        bytes32 _id,   // Id of the Loan
        uint256 _amount,
        address _origin,
        bytes calldata _oracleData
    ) external returns (uint256 paid, uint256 paidToken)

~~~

### Amount

This parameter refers to the amount entered to pay of the debt. The function checks that the borrower doesn't pay more than the pending debt, although a greater amount has been entered.

### Origin

The origin refers to the address who is paying for the debt.  

### 

### Oracle Data

The Oracle data holds information about the currency of the loan and the RCN rate, which is use to convert the currency amount to RCN tokens amount. 

~~~ javascript
// How to get oracle Data 

// creates oracle contract instance
const oracleContract = web3.eth.contract(OracleAbi).at(oracle.address);
// returns oracle contract url 
const url = await oracleContract.url();
// Oracle response
const oracleResponse = await this.http.get(url).toPromise() as any[];

// Example

url = https://oracle.ripio.com/rate/
// Oracle example response at the moment of the get request
oracleRespose = [
  {
    "currency": "0x4152530000000000000000000000000000000000000000000000000000000000", //ARS
    "data": "0x000000000000000000000000000000000000000000000000000000005c6c267e0000000000000000000000000000000000000000000000001f0b048c850853000000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000001cd4d0c067a01947458be243373c4ddcf818ef94cf71e345df1180a9ff092e94b7473f21763b1a8c9b020a4114895b0d8bb5ce03944a110cec20b019f869f89a61", 
    "decimals": 2, 
    "oracle": "0x22222c1944EfCC38CA46489f96c3A372C4dB74E6", 
    "r": "0xd4d0c067a01947458be243373c4ddcf818ef94cf71e345df1180a9ff092e94b7", 
    "rate": 2236886641493431040, 
    "s": "0x473f21763b1a8c9b020a4114895b0d8bb5ce03944a110cec20b019f869f89a61", 
    "timestamp": 1550591614, 
    "v": 28
  }, 
  ...,
  ...  
]

oracleData = oracleResponse.data;

~~~

If the address of the oracle is equal to address '0x0' the currency is RCN, so no conversion is needed.

###

### Example

~~~ javascript
// Pay loan example 

// Partial Pay
const payTransaction = await debtEngine.pay(
          '0x86029ff516bbfe74ad2c96e90a18d9b3e984d2152a10824ab0ee4521ab952728', // Id of the loan     
          web3.utils.toWei("100", "ether"),     // equal to = '100000000000000000000' RCN tokens
          accounts[3],                       // origin Address
          [],                                // oracle data not provided
          { from: accounts[3] });            //Sender Addres


// payment is added and the balance of the debt is updated.

// Get debt of loan 
debt = await debtEngine.debts(id);

debt:
{ id: '0x86029ff516bbfe74ad2c96e90a18d9b3e984d2152a10824ab0ee4521ab952728', // Loan Id
   error: false,                                          // error flag  
   balance: '100000000000000000000',                      // amount already payed of the debt       
   model: '0xf1d88d1a22AD6D4A56137761e8df4aa68eDa3A11',   // Model Address        
   creator: '0x275b0DC17674e02a8a434689A638E98D9aCd417a', // Loan Manager Address 
   oracle: '0x0000000000000000000000000000000000000000',  // Oracle address
} 

~~~

###