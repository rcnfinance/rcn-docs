---
id: cancel-request
title: Cancel Request 
sidebar_label: Cancel Request 
---

The point of entry to cancel a loan request is the Loan Manager. 

Only borrower or creator can cancel a request and the request should be open.


## Cancel request function

~~~ javascript
    
// Cancel function interface   

function cancel(
  bytes32 _id   // ID of the loan request
  ) 
external returns (bool)   // returns true if success
~~~


### Example

~~~ javascript
// Cancel request example 

  // Cancel request 
await loanManager.cancel(
  '0x65b981e1a452c2e4fe02e54e1ec2f3a1cc241522f02e4235eb8b44f2a29635f3', //Id of the loan request
  { from: accounts[0] }      // sender should be the creator or the borrower
  );  
~~~

###