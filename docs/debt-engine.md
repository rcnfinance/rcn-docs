---
id: debt-engine
title: Debt engine
sidebar_label: Debt engine
---

## Create a debt

Creating a debt entry on the DebtEngine contract can be done calling the *create* method, this method will emit an ERC721 asset representing the debt and assign it to the *owner* specified on the creation parameters.

The DebtEngine will create the registry of the debt on the Model using the provided creation data, the model defines the creation data scheme, and the call will fail if the model rejects the creation or if the model is invalid.

> **Notice:** Any Ethereum address can create a debt; consequently a debt originated by an unknown address should not be treated as a valid liability.

#### Debt Id

A bytes32 hash id identifies each Debt; there are three different methods to create debts on the Engine, and each one of them will result in a different scheme for the ID.

The id of debt is always deterministic; therefore it can be known before creating the debt; allowing to perform different operations on the same debt without waiting for the execution of the previous calls.

~~~
id = 0xe821bedc516cb23f998d0d616fd71d6ac55bfde80559a73696edcdb90a65004b
~~~

### Function: create


TODO;