---
id: lend
title: Lend 
sidebar_label: Lend 
---

The point of entry to lend is the LoanManager. This contract allows the lender to complete a loan application, send tokens to the borrower and creates the resulting debt in the Debt Engine contract.

The lender has to set all the required parameters to perform lending. Some of the requirements to be able to lend are: The loan request should be open, 
approved by the borrower, not expired and the lender should have enough funds. 

### Lend function interface

~~~ javascript
// Lend function interfece

function lend(
        bytes32 _id,        
        bytes memory _oracleData, 
        address _cosigner,
        uint256 _cosignerLimit,
        bytes memory _cosignerData
    ) public returns (bool)

~~~

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

~~~

If the address of the oracle is equal to address '0x0' the currency is RCN, so no convertion is needed and the amount is return.

### Cosigner

The lender can include a cosigner at the moment of lending. This cosigner address acts as a guarantee and will take responsibility in case the borrower defaults the loan payment.

### Cosigner Limit 

The cosigner limit refers to the maximum amount that the lender is willing to pay the cosigner for the aditional cost that implies. 

### 

### Cosigner Data 

The cosigner data holds information about the cosigner added by the lender. 

### 

### Example

~~~ javascript
// Lend loan example 

const lendTransaction = await loanManager.lend(
            '', // Loan Id
            [],                 // O0x86029ff516bbfe74ad2c96e90a18d9b3e984d2152a10824ab0ee4521ab952728racleData
            '0x0000000000000000000000000000000000000000',   // Cosigner  0x address
            '0', // Cosigner limit
            [],                 // Cosigner data 
            { from: accounts[1] }    // Owner/Lender
        );   

// debt Created -- the lend function in Loan Manager calls the function: 
// create2(Model _model, address _owner, address _oracle, uint256 _salt, bytes calldata _data) external returns (bytes32 id)
// of the Debt Engine Contract creating the debt.

debt:
{ id: '0x86029ff516bbfe74ad2c96e90a18d9b3e984d2152a10824ab0ee4521ab952728', // Loan Id
   error: false,                                          // error flag  
   balance: '0',                                         // amount already payed of the debt       
   model: '0xf1d88d1a22AD6D4A56137761e8df4aa68eDa3A11',   // Model Address        
   creator: '0x275b0DC17674e02a8a434689A638E98D9aCd417a', // Loan Manager Address 
   oracle: '0x0000000000000000000000000000000000000000',  // Oracle address
} 

// Get debt of loan 
debt = await debtEngine.debts(id);

~~~

In the Debt Engine 'create2' function "model.create(id,data)" is call , which creates the structure and necessary data of the loan in the model contract. This depends on the model being use when the loan was requested and how the "create(id, data)" function is implemented.

###