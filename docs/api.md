---
id: api
title: API
sidebar_label: API
---


## Debts


### Fetching debts

    GET /v4/debts/

#### Query parameters:

| Field     | Type    | Description                                             | Optional |
|-----------|---------|---------------------------------------------------------|----------|
| error     | boolean | Get a list of debts with error equal than this value    | Yes      |
| model     | string  | Get a list of debts with model equal than this value    | Yes      |
| creator   | string  | Get a list of debts with creator equal than this value  | Yes      |
| oracle    | string  | Get a list of debts with oracle equal than this value   | Yes      |
| page_size | integer | Get a list of config with n items                       | Yes      |
| page      | integer | Get the nth page of configs                             | Yes      |

#### Response

##### 200

```json
{
    "meta": {
        "params": {
            "indent": 0,
            "page_size": 10,
            "page": 0
        },
        "page_size": 10,
        "page": 0,
        "prev": null,
        "next": "page=1&page_size=10"
    },
    "content": [
        {
            "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
            "error": false,
            "balance": "0",
            "model": "0xE3633E63Da6154D9450e34F0d4c64c6A51f6918e",
            "creator": "0xbF77a4061eB243d38BaCBD684f0c3124eefE6E91",
            "oracle": "0x0000000000000000000000000000000000000000",
            "commits": [
                {
                    "opcode": "created_debt_engine",
                    "timestamp": 1541796770,
                    "order": 6,
                    "proof": "0xfe6eac4a8a88695d43e71089af2554742716fbe25c3f1509a49ac0c1bf386eca",
                    "data": {
                        "_data": "0x7150d59760a6784ebc4325f4f77908df62855551d861ade1b1553e731b9b32e30000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000003c00000000000000000f43fc2c04ee000000000000000000000000000000000000000000000000000000001792f86480c800000c00000151800000003c",
                        "error": false,
                        "balance": "0",
                        "model": "0xE3633E63Da6154D9450e34F0d4c64c6A51f6918e",
                        "creator": "0xbF77a4061eB243d38BaCBD684f0c3124eefE6E91",
                        "oracle": "0x0000000000000000000000000000000000000000",
                        "created": "1541796770",
                        "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21"
                    }
                }
            ]
        },
        ...
    ]
}
```


### Fetching a debt

    GET /v4/debts/:id/

#### Response

##### 200

```json
{
    "meta": {
        "params": {
            "indent": 0
        }
    },
    "content": {
        "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
        "error": false,
        "balance": "0",
        "model": "0xE3633E63Da6154D9450e34F0d4c64c6A51f6918e",
        "creator": "0xbF77a4061eB243d38BaCBD684f0c3124eefE6E91",
        "oracle": "0x0000000000000000000000000000000000000000",
        "commits": [
            {
                "opcode": "created_debt_engine",
                "timestamp": 1541796770,
                "order": 6,
                "proof": "0xfe6eac4a8a88695d43e71089af2554742716fbe25c3f1509a49ac0c1bf386eca",
                "data": {
                    "_data": "0x7150d59760a6784ebc4325f4f77908df62855551d861ade1b1553e731b9b32e30000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000003c00000000000000000f43fc2c04ee000000000000000000000000000000000000000000000000000000001792f86480c800000c00000151800000003c",
                    "error": false,
                    "balance": "0",
                    "model": "0xE3633E63Da6154D9450e34F0d4c64c6A51f6918e",
                    "creator": "0xbF77a4061eB243d38BaCBD684f0c3124eefE6E91",
                    "oracle": "0x0000000000000000000000000000000000000000",
                    "created": "1541796770",
                    "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21"
                }
            }
        ]
    }
}
```

##### 404

```json
{
    "title": "Debt does not exists",
    "description": "Debt with id=x does not exists"
}
```

## Configs

### Fetching configs

    GET /v4/configs/

#### Query parameters:

| Field     | Type    | Description                       | Optional |
|-----------|---------|-----------------------------------|----------|
| page_size | integer | Get a list of config with n items | Yes      |
| page      | integer | Get the nth page of configs       | Yes      |

#### Response

```json
{
    "meta": {
        "params": {
            "indent": 0,
            "page_size": 10,
            "page": 0
        },
        "page_size": 10,
        "page": 0,
        "prev": null,
        "next": "page=1&page_size=10"
    },
    "content": [
        {
            "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
            "data": {
                "installments": 12,
                "timeUnit": 60,
                "duration": 86400,
                "lentTime": 1541796770,
                "cuota": 1100000000000000000,
                "interestRate": 25920000000200
            },
            "commits": [
                {
                    "opcode": "created_installments",
                    "timestamp": 1541796770,
                    "order": 4,
                    "proof": "0xfe6eac4a8a88695d43e71089af2554742716fbe25c3f1509a49ac0c1bf386eca",
                    "data": {
                        "installments": 12,
                        "timeUnit": 60,
                        "duration": 86400,
                        "lentTime": 1541796770,
                        "cuota": 1100000000000000000,
                        "interestRate": 25920000000200
                    }
                }
            ]
        },
    ]
}
```


### Fetching a config

    GET /v4/configs/:id/

#### Response

##### 200

```json
{
    "meta": {
        "params": {
            "indent": 0
        }
    },
    "content": {
        "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
        "data": {
            "installments": 12,
            "timeUnit": 60,
            "duration": 86400,
            "lentTime": 1541796770,
            "cuota": 1100000000000000000,
            "interestRate": 25920000000200
        },
        "commits": [
            {
                "opcode": "created_installments",
                "timestamp": 1541796770,
                "order": 4,
                "proof": "0xfe6eac4a8a88695d43e71089af2554742716fbe25c3f1509a49ac0c1bf386eca",
                "data": {
                    "installments": 12,
                    "timeUnit": 60,
                    "duration": 86400,
                    "lentTime": 1541796770,
                    "cuota": 1100000000000000000,
                    "interestRate": 25920000000200
                }
            }
        ]
    }
}
```

##### 404

```json
{
    "title": "Config does not exists",
    "description": "Config with id=x does not exists"
}
```

## Loans

### Fetching loans

    GET /v4/loans/

#### Query parameters:

| Field     | Type    | Description                                                | Optional |
|-----------|---------|------------------------------------------------------------|----------|
| open      | boolean | Get a list of loans with error equal than this value    | Yes      |
| approved  | boolean | Get a list of loans with approved equal than this value | Yes      |
| cosigner  | string  | Get a list of loans with cosigner equal than this value | Yes      |
| model     | string  | Get a list of loans with model equal than this value    | Yes      |
| creator   | string  | Get a list of loans with creator equal than this value  | Yes      |
| oracle    | string  | Get a list of loans with oracle equal than this value   | Yes      |
| borrower  | string  | Get a list of loans with borrower equal than this value | Yes      |
| canceled  | boolean | Get a list of loans with canceled equal than this value | Yes      |
| status    | string  | Get a list of loans with status equal than this value      | Yes      |
| page_size | integer | Get a list of config with n items                          | Yes      |
| page      | integer | Get the nth page of configs                                | Yes      |

#### Response

##### 200

```json
{
    "meta": {
        "params": {
            "indent": 0,
            "page_size": 10,
            "page": 0
        },
        "page_size": 10,
        "page": 0,
        "prev": null,
        "next": "page=1&page_size=10"
    },
    "content": [
        {
            "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
            "open": false,
            "approved": true,
            "position": "0",
            "expiration": "3136633892082024447",
            "amount": "12000000000000000000",
            "cosigner": "0x0",
            "model": "0xE3633E63Da6154D9450e34F0d4c64c6A51f6918e",
            "creator": "0x06779a9848e5Df60ce0F5f63F88c5310C4c7289C",
            "oracle": "0x0000000000000000000000000000000000000000",
            "borrower": "0x06779a9848e5Df60ce0F5f63F88c5310C4c7289C",
            "salt": "51254173808193647528491371025376947732924163382010321361587123973758161466083",
            "loanData": "00000000000000000f43fc2c04ee000000000000000000000000000000000000000000000000000000001792f86480c800000c00000151800000003c",
            "created": "1541796210",
            "descriptor": {
                "first_obligation": "1100000000000000000",
                "total_obligation": "13200000000000000000",
                "duration": "1036800",
                "interest_rate": "298.6111111111114",
                "punitive_interest_rate": "25920000000200",
                "frequency": "86400",
                "installments": "12"
            },
            "currency": "0000000000000000000000000000000000000000000000000000000000000000",
            "status": "1",
            "commits": [
                {
                    "opcode": "requested_loan_manager",
                    "timestamp": 1541796210,
                    "order": 0,
                    "proof": "0xb040d83bacf5a18a74704d41c391cebe92d0c5955597cc8c9871acae4c3b4794",
                    "data": {
                        "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
                        "open": true,
                        "approved": true,
                        "position": "0",
                        "expiration": "3136633892082024447",
                        "amount": "12000000000000000000",
                        "cosigner": "0x0",
                        "model": "0xE3633E63Da6154D9450e34F0d4c64c6A51f6918e",
                        "creator": "0x06779a9848e5Df60ce0F5f63F88c5310C4c7289C",
                        "oracle": "0x0000000000000000000000000000000000000000",
                        "borrower": "0x06779a9848e5Df60ce0F5f63F88c5310C4c7289C",
                        "salt": "51254173808193647528491371025376947732924163382010321361587123973758161466083",
                        "loanData": "00000000000000000f43fc2c04ee000000000000000000000000000000000000000000000000000000001792f86480c800000c00000151800000003c",
                        "created": "1541796210",
                        "descriptor": {
                            "first_obligation": "1100000000000000000",
                            "total_obligation": "13200000000000000000",
                            "duration": "1036800",
                            "interest_rate": "298.6111111111114",
                            "punitive_interest_rate": "25920000000200",
                            "frequency": "86400",
                            "installments": "12"
                        },
                        "currency": "0000000000000000000000000000000000000000000000000000000000000000",
                        "status": "1"
                    }
                },
                {
                    "opcode": "approved_loan_manager",
                    "timestamp": 1541796210,
                    "order": 1,
                    "proof": "0xb040d83bacf5a18a74704d41c391cebe92d0c5955597cc8c9871acae4c3b4794",
                    "data": {
                        "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
                        "approved": true
                    }
                },
                {
                    "opcode": "lent_loan_manager",
                    "timestamp": 1541796770,
                    "order": 3,
                    "proof": "0xfe6eac4a8a88695d43e71089af2554742716fbe25c3f1509a49ac0c1bf386eca",
                    "data": {
                        "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
                        "lender": "0x00000000000000000000000006779a9848e5df60ce0f5f63f88c5310c4c728",
                        "tokens": "9c000000000000000000000000000000000000000000000000a688906bd8b000",
                        "open": false
                    }
                }
            ]
        },
        ...
    ]
}
```


### Fetching a loan

    GET /v4/loans/:id/

#### Response

##### 200

```json
{
    "meta": {
        "params": {
            "indent": 0
        }
    },
    "content": {
        "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
        "open": false,
        "approved": true,
        "position": "0",
        "expiration": "3136633892082024447",
        "amount": "12000000000000000000",
        "cosigner": "0x0",
        "model": "0xE3633E63Da6154D9450e34F0d4c64c6A51f6918e",
        "creator": "0x06779a9848e5Df60ce0F5f63F88c5310C4c7289C",
        "oracle": "0x0000000000000000000000000000000000000000",
        "borrower": "0x06779a9848e5Df60ce0F5f63F88c5310C4c7289C",
        "salt": "51254173808193647528491371025376947732924163382010321361587123973758161466083",
        "loanData": "00000000000000000f43fc2c04ee000000000000000000000000000000000000000000000000000000001792f86480c800000c00000151800000003c",
        "created": "1541796210",
        "descriptor": {
            "first_obligation": "1100000000000000000",
            "total_obligation": "13200000000000000000",
            "duration": "1036800",
            "interest_rate": "298.6111111111114",
            "punitive_interest_rate": "25920000000200",
            "frequency": "86400",
            "installments": "12"
        },
        "currency": "0000000000000000000000000000000000000000000000000000000000000000",
        "status": "1",
        "commits": [
            {
                "opcode": "requested_loan_manager",
                "timestamp": 1541796210,
                "order": 0,
                "proof": "0xb040d83bacf5a18a74704d41c391cebe92d0c5955597cc8c9871acae4c3b4794",
                "data": {
                    "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
                    "open": true,
                    "approved": true,
                    "position": "0",
                    "expiration": "3136633892082024447",
                    "amount": "12000000000000000000",
                    "cosigner": "0x0",
                    "model": "0xE3633E63Da6154D9450e34F0d4c64c6A51f6918e",
                    "creator": "0x06779a9848e5Df60ce0F5f63F88c5310C4c7289C",
                    "oracle": "0x0000000000000000000000000000000000000000",
                    "borrower": "0x06779a9848e5Df60ce0F5f63F88c5310C4c7289C",
                    "salt": "51254173808193647528491371025376947732924163382010321361587123973758161466083",
                    "loanData": "00000000000000000f43fc2c04ee000000000000000000000000000000000000000000000000000000001792f86480c800000c00000151800000003c",
                    "created": "1541796210",
                    "descriptor": {
                        "first_obligation": "1100000000000000000",
                        "total_obligation": "13200000000000000000",
                        "duration": "1036800",
                        "interest_rate": "298.6111111111114",
                        "punitive_interest_rate": "25920000000200",
                        "frequency": "86400",
                        "installments": "12"
                    },
                    "currency": "0000000000000000000000000000000000000000000000000000000000000000",
                    "status": "1"
                }
            },
            {
                "opcode": "approved_loan_manager",
                "timestamp": 1541796210,
                "order": 1,
                "proof": "0xb040d83bacf5a18a74704d41c391cebe92d0c5955597cc8c9871acae4c3b4794",
                "data": {
                    "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
                    "approved": true
                }
            },
            {
                "opcode": "lent_loan_manager",
                "timestamp": 1541796770,
                "order": 3,
                "proof": "0xfe6eac4a8a88695d43e71089af2554742716fbe25c3f1509a49ac0c1bf386eca",
                "data": {
                    "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
                    "lender": "0x00000000000000000000000006779a9848e5df60ce0f5f63f88c5310c4c728",
                    "tokens": "9c000000000000000000000000000000000000000000000000a688906bd8b000",
                    "open": false
                }
            }
        ]
    }
}
```

##### 404

```json
{
    "title": "Loan does not exists",
    "description": "Loan with id=x does not exists"
}
```

## Oracle History

### Fetching oracle history

    GET /v4/oracle_history/

#### Query parameters:

| Field     | Type    | Description                       | Optional |
|-----------|---------|-----------------------------------|----------|
| page_size | integer | Get a list of config with n items | Yes      |
| page      | integer | Get the nth page of configs       | Yes      |


#### Response

##### 200

```json
{
    "meta": {
        "params": {
            "indent": 0,
            "page_size": 10,
            "page": 0
        },
        "page_size": 10,
        "page": 0,
        "prev": null,
        "next": "page=1&page_size=10"
    },
    "content": [
        {
            "id": "0x27e5541d54da6f916d8eb8cf905870d6980a1328972e8a85e4d03c8c55cb5f9b",
            "tokens": "6523",
            "equivalent": "9496",
            "timestamp": "223507755.0"
        },
        {
            "id": "0x27e5541d54da6f916d8eb8cf905870d6980a1328972e8a85e4d03c8c55cb5f9b",
            "tokens": "2381",
            "equivalent": "848",
            "timestamp": "1389779792.0"
        }
    ]
}
```


### Fetching a oracle history

    GET /v4/oracle_history/:id

##### 200

```json
{
    "meta": {
        "params": {
            "indent": 0
        }
    },
    "content": {
        "id": "0x27e5541d54da6f916d8eb8cf905870d6980a1328972e8a85e4d03c8c55cb5f9b",
        "tokens": "2381",
        "equivalent": "848",
        "timestamp": "1389779792.0"
    }
}
```

##### 404

```json
{
    "title": "History does not exists",
    "description": "History with id=x does not exists"
}
```


## States

### Fetching states

    GET /v4/states/

#### Query parameters:

| Field     | Type    | Description                       | Optional |
|-----------|---------|-----------------------------------|----------|
| page_size | integer | Get a list of config with n items | Yes      |
| page      | integer | Get the nth page of configs       | Yes      |
| status    | string  | Get states by status code         | Yes      | 


#### Response

##### 200

```json
{
    "meta": {
        "params": {
            "indent": 0,
            "page_size": 10,
            "page": 0
        },
        "page_size": 10,
        "page": 0,
        "prev": null,
        "next": "page=1&page_size=10"
    },
    "content": [
        {
            "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
            "status": "0",
            "clock": "86400",
            "last_payment": "0",
            "paid": "0",
            "paid_base": "0",
            "interest": "0",
            "commits": [
                {
                    "opcode": "set_clock_installments",
                    "timestamp": 1541796770,
                    "order": 5,
                    "proof": "0xfe6eac4a8a88695d43e71089af2554742716fbe25c3f1509a49ac0c1bf386eca",
                    "data": {
                        "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
                        "duration": "86400"
                    }
                }
            ]
        },
        {
            "id": "0x3c51b239bb507123a3568b5f47bba8fa811a9dc6caec186b359d049acbdb3cdd",
            "status": "0",
            "clock": "2592000",
            "last_payment": "0",
            "paid": "0",
            "paid_base": "0",
            "interest": "0",
            "commits": [
                {
                    "opcode": "set_clock_installments",
                    "timestamp": 1541800628,
                    "order": 23,
                    "proof": "0x724431327264c2d4b8ebcd0f525e4d67c6c637bd51a77c09ad7366e333ee0738",
                    "data": {
                        "id": "0x3c51b239bb507123a3568b5f47bba8fa811a9dc6caec186b359d049acbdb3cdd",
                        "duration": "2592000"
                    }
                }
            ]
        },
        {
            "id": "0x542bd1db5afae2cf83dd540c78edbed13a5df9c3d2149ba2ef9d2d045094f39d",
            "status": "0",
            "clock": "2592000",
            "last_payment": "0",
            "paid": "0",
            "paid_base": "0",
            "interest": "0",
            "commits": [
                {
                    "opcode": "set_clock_installments",
                    "timestamp": 1542835829,
                    "order": 31,
                    "proof": "0x533ebcd42e0cdfb2ef729ca671fb66235dbc2f03406789c6875a63bc650eafc8",
                    "data": {
                        "id": "0x542bd1db5afae2cf83dd540c78edbed13a5df9c3d2149ba2ef9d2d045094f39d",
                        "duration": "2592000"
                    }
                }
            ]
        }
    ]
}
```


### Fetching a state

    GET /v4/states/:id

##### 200

```json
{
    "meta": {
        "params": {
            "indent": 0
        }
    },
    "content": {
        "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
        "status": "0",
        "clock": "86400",
        "last_payment": "0",
        "paid": "0",
        "paid_base": "0",
        "interest": "0",
        "commits": [
            {
                "opcode": "set_clock_installments",
                "timestamp": 1541796770,
                "order": 5,
                "proof": "0xfe6eac4a8a88695d43e71089af2554742716fbe25c3f1509a49ac0c1bf386eca",
                "data": {
                    "id": "0xf2523c4a6574f570726a7b937321ea98f31f7274ecbe707a1d50ce3e1dbd0d21",
                    "duration": "86400"
                }
            }
        ]
    }
}
```

##### 404

```json
{
    "title": "State does not exists",
    "description": "State with id=X does not exists"
}
```


## Model Debt Info

### Fetching a model info

    GET /v4/model_debt_info/:id

##### 200

```json
{
    "paid": 0,
    "dueTime": 1541883170,
    "estimatedObligation": 13442944166664979548,
    "nextObligation": 1100000000000000000,
    "currentObligation": 13442944166664979548,
    "debtBalance": "0",
    "owner": "0x06779a9848e5Df60ce0F5f63F88c5310C4c7289C"
}
```

##### 404

```json
{
    "title": "Debt does not exist",
    "description": "Debt with id=X does not exist"
}
```


