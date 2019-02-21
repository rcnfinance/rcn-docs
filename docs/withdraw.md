---
id: withdraw
title: Withdraw 
sidebar_label: Withdraw 
---

The point of entry to withdraw from a loan is the Debt Engine. This functions allows any authorized sender address, to withdraw tokens for the receiving address.

The authorized sender can withdraw part or the total of the available withdrawal amount.

## Withdraw functions

~~~ javascript
//withdraw function interface

function withdraw(
    bytes32 _id,    // Loan Id
    address _to     // reciever address of withdrawal amount  
    )     
    external returns (uint256 amount) 
    
    
// partial withdraw function interface    
function withdrawPartial(
    bytes32 _id,
    address _to, 
    uint256 _amount  //amount to withdraw
    )  
    external returns (bool success)
~~~

### Reciever Address (_to)

This parameter refers to the address that the tokens are transfered to.

### Withdrawal amount (_amount)

In the "withdrawPartial" function it is posible to define a partial amount to withdraw of the available withdrawal amount.

### 

### Example

~~~ javascript
// Withdraw example 

previousBalanceOfAddress = await rcnToken.balanceOf(accounts[1]);

// Partial Withdraw
const withdrawTransaction = await debtEngine.withdrawPartial(
    '0x86029ff516bbfe74ad2c96e90a18d9b3e984d2152a10824ab0ee4521ab952728', // Id of the Loan                                       
    accounts[1],                                 // reciever account of the withdrawal amount   
    web3.utils.toWei("20", "ether"),            // Amount to withdraw equal to = '20000000000000000000'
    { from: accounts[1] });                     // sender address Should be authorized  


// funds are transfer to the _to(accounts[1]) address and the balance is updated

// balance of accounts[1]
newBalanceOfAddress = await rcnToken.balanceOf(accounts[1]);

// The newBalanceOfAddress is equal to the previousBalanceOfAddress + withdraw amount

// If previousBalanceOfAddress = 0 the newBalanceOfAddress should be:
newBalanceOfAddress = '20000000000000000000' // the amount withdrawn
~~~

###