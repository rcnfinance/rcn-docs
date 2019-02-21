---
id: transfer
title: Transfer 
sidebar_label: Transfer 
---

The point of entry to transfer a loan debt is the Debt Engine. The debt Engine inherits this functionality from the ERC721 contract which is used to handle assets.

This function allows the transfer of ownership of a debt. The sender should be authorized to transfer the debt from one owner to another.

## Transfer function

~~~ javascript
    
    // Transfer function interface   

    function safeTransferFrom(
        address _from,  
        address _to,    
        uint256 _assetId) // Id of the loan/debt 
        external
~~~

### Debt owner address (_from)

This parameter refers to the address that currently owns the debt.

### Reciever address (_to)

This parameter refers to the address to receive the ownership of the debt.

### 

### Example

~~~ javascript
// Transfer debt example 

  // Transfer debt 
      await debtEngine.safeTransferFrom(
          accounts[1],         // address that currently owns the debt
          accounts[2],         // address to receive the ownership of the debt
          '0x86029ff516bbfe74ad2c96e90a18d9b3e984d2152a10824ab0ee4521ab952728', // Id of the loan/debt 
          {from: accounts[1] });   // sender address should be authorized to transfer the debt

    newOwner =  await loanManager.ownerOf('0x86029ff516bbfe74ad2c96e90a18d9b3e984d2152a10824ab0ee4521ab952728');

  // newOwner should be equal to accounts[2]

~~~

###