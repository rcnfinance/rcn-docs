---
id: credit
title: Credit Contract
sidebar_label: Credit Contract
---

## Credit Contract



#### Definition

It is the contract that contains the conditions agreed between the parties.
It manages the logic of the agreement with which the funds will be handled between them.

Each type of credit contract contains the agreed logic within which there are
certain variables that are parametrizable. When the contract is agreed,
an instance is generated in which the values of these parameters are defined
 and the agents sign the agreement.



#### Rational

The essential purpose of these contracts is to record the agreed conditions
 in a transparent and immutable manner.

In particular, it identifies who are the agents that make the agreement,
regulates the amount of money of the loan, the currency in which the debt
is denominated, in how many installments and on what dates the loan will be returned,
the portion of principal and interest of each installment, penalties in case of delay,
fees of different agents, etc.



#### Representation

In RCN this credit contract is implemented as a smart contract (https://github.com/ethereum/wiki/wiki/White-Paper).
This is self-executing contracts with the terms of the agreement.
Each contract has a hash that acts as ID and uniquely identifies it over the network.

Generally, although not necessarily, the Borrower is the one who creates the smart contract by publishing a loan request with which the flow begins on the network.
Then this contract is signed by the other agents and changes its status according to the stage of the debt.

Example:  
https://deploy-preview-144--rcn-loans-ropsten-live.netlify.com/loan/0x3c51b239bb507123a3568b5f47bba8fa811a9dc6caec186b359d049acbdb3cdd



