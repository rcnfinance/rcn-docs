# API

## Fetching debts

    GET /v4/debts/

### Query parameters:

| Field     | Type    | Description                                             | Optional |
|-----------|---------|---------------------------------------------------------|----------|
| error     | boolean | Get a list of debts with error equal than this value    | Yes      |
| currency  | string  | Get a list of debts with currency equal than this value | Yes      |
| model     | string  | Get a list of debts with model equal than this value    | Yes      |
| creator   | string  | Get a list of debts with creator equal than this value  | Yes      |
| oracle    | string  | Get a list of debts with oracle equal than this value   | Yes      |
| page_size | integer | Get a list of config with n items                       | Yes      |
| page      | integer | Get the nth page of configs                             | Yes      |

### Response

#### 200

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
            "error": false,
            "currency": "0000000000000000",
            "balance": "0",
            "model": "0x25E9746E5E76A75C90E895d1ed4Ad39355bdf9ad",
            "creator": "0x80B9847b2446A9d179a5cc77f138A6Babca87f1D",
            "oracle": "0x0000000000000000000000000000000000000000",
            "commits": [
                {
                    "opcode": "created_debt_engine",
                    "timestamp": 1539849581,
                    "order": 2,
                    "proof": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4b",
                    "data": {
                        "_data": "0x261ef5fb3fe3b7253c5fec6fd0ef312402c9cd97530516aef13241e23274f8e60000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000003c000000000000000006f05b59d3b200000000000000000000000000000000000000000000000000000000096dfcf5000000001e00000151800000000b",
                        "error": false,
                        "currency": "0000000000000000",
                        "balance": "0",
                        "model": "0x25E9746E5E76A75C90E895d1ed4Ad39355bdf9ad",
                        "creator": "0x80B9847b2446A9d179a5cc77f138A6Babca87f1D",
                        "oracle": "0x0000000000000000000000000000000000000000",
                        "created": "1539849581",
                        "id": "0x27e5541d54da6f916d8eb8cf905870d6980a1328972e8a85e4d03c8c55cb5f9b"
                    }
                }
            ]
        },
        ...
    ]
}
```


## Fetching a debt

    GET /v4/debts/:id/

### Response

#### 200

```json
{
    "meta": {
        "params": {
            "indent": 0
        }
    },
    "content": {
        "id": "0x27e5541d54da6f916d8eb8cf905870d6980a1328972e8a85e4d03c8c55cb5f9b",
        "error": false,
        "currency": "0000000000000000",
        "balance": "0",
        "model": "0x25E9746E5E76A75C90E895d1ed4Ad39355bdf9ad",
        "creator": "0x80B9847b2446A9d179a5cc77f138A6Babca87f1D",
        "oracle": "0x0000000000000000000000000000000000000000",
        "commits": [
            {
                "opcode": "created_debt_engine",
                "timestamp": 1539849581,
                "order": 2,
                "proof": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4b",
                "data": {
                    "_data": "0x261ef5fb3fe3b7253c5fec6fd0ef312402c9cd97530516aef13241e23274f8e60000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000003c000000000000000006f05b59d3b200000000000000000000000000000000000000000000000000000000096dfcf5000000001e00000151800000000b",
                    "error": false,
                    "currency": "0000000000000000",
                    "balance": "0",
                    "model": "0x25E9746E5E76A75C90E895d1ed4Ad39355bdf9ad",
                    "creator": "0x80B9847b2446A9d179a5cc77f138A6Babca87f1D",
                    "oracle": "0x0000000000000000000000000000000000000000",
                    "created": "1539849581",
                    "id": "0x27e5541d54da6f916d8eb8cf905870d6980a1328972e8a85e4d03c8c55cb5f9b"
                }
            }
        ]
    }
}
```

#### 404

```json
{
    "title": "Debt does not exists",
    "description": "Debt with id=x does not exists"
}
```


## Fetching configs

    GET /v4/configs/

### Query parameters:

| Field     | Type    | Description                       | Optional |
|-----------|---------|-----------------------------------|----------|
| page_size | integer | Get a list of config with n items | Yes      |
| page      | integer | Get the nth page of configs       | Yes      |

### Response

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
            "data": {
                "installments": 30,
                "duration": 11,
                "lentTime": 86400,
                "cuota": 1539849581,
                "interestRate": 500000000000000000,
                "timeUnit": [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,9,109,252,245,0,0]
            },
            "commits": [
                {
                    "opcode": "created_installments",
                    "timestamp": 1539849581,
                    "order": 0,
                    "proof": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4b",
                    "data": {
                        "installments": 30,
                        "duration": 11,
                        "lentTime": 86400,
                        "cuota": 1539849581,
                        "interestRate": 500000000000000000,
                        "timeUnit": [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,9,109,252,245,0,0]
                    }
                }
            ]
        }
    ]
}
```


## Fetching a config

    GET /v4/configs/:id/

### Response

#### 200

```json
{
    "meta": {
        "params": {
            "indent": 0
        }
    },
    "content": {
        "id": "0x27e5541d54da6f916d8eb8cf905870d6980a1328972e8a85e4d03c8c55cb5f9b",
        "data": {
            "installments": 30,
            "duration": 11,
            "lentTime": 86400,
            "cuota": 1539849581,
            "interestRate": 500000000000000000,
            "timeUnit": [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,9,109,252,245,0,0]
        },
        "commits": [
            {
                "opcode": "created_installments",
                "timestamp": 1539849581,
                "order": 0,
                "proof": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4b",
                "data": {
                    "installments": 30,
                    "duration": 11,
                    "lentTime": 86400,
                    "cuota": 1539849581,
                    "interestRate": 500000000000000000,
                    "timeUnit": [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,9,109,252,245,0,0]
                }
            }
        ]
    }
}
```

#### 404

```json
{
    "title": "Config does not exists",
    "description": "Config with id=x does not exists"
}
```


## Fetching requests

    GET /v4/requests/

### Query parameters:

| Field     | Type    | Description                                                | Optional |
|-----------|---------|------------------------------------------------------------|----------|
| open      | boolean | Get a list of requests with error equal than this value    | Yes      |
| approved  | boolean | Get a list of requests with approved equal than this value | Yes      |
| cosigner  | string  | Get a list of requests with cosigner equal than this value | Yes      |
| model     | string  | Get a list of requests with model equal than this value    | Yes      |
| creator   | string  | Get a list of requests with creator equal than this value  | Yes      |
| oracle    | string  | Get a list of requests with oracle equal than this value   | Yes      |
| borrower  | string  | Get a list of requests with borrower equal than this value | Yes      |
| canceled  | boolean | Get a list of requests with canceled equal than this value | Yes      |
| page_size | integer | Get a list of config with n items                          | Yes      |
| page      | integer | Get the nth page of configs                                | Yes      |

### Response

#### 200

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
            "id": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4b",
            "open": false,
            "approved": false,
            "position": "8193",
            "expiration": "240056125.0",
            "amount": "3298",
            "cosigner": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4b",
            "model": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4c",
            "creator": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4d",
            "oracle": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea43",
            "borrower": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4f",
            "salt": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91eagb",
            "loanData": "b'Nqf\\xef\\x19\\xdbC\\x07\\xbbb\\xe1\\x1c\\xcd\\xac\\xf8U=\\x18\\xf1\\xd5\\xd4\\xdf\\xc5\\x1f'",
            "canceled": true,
            "created": "505026943.0",
            "commits": [
                {
                    "opcode": "asd",
                    "timestamp": 172811475,
                    "order": 4,
                    "proof": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4b",
                    "data": {
                        "value": "pepito"
                    }
                }
            ]
        },
        ...
    ]
}
```


## Fetching a request

    GET /v4/requests/:id/

### Response

#### 200

```json
{
    "meta": {
        "params": {
            "indent": 0
        }
    },
    "content": {
        "id": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4b",
            "open": false,
            "approved": false,
            "position": "8193",
            "expiration": "240056125.0",
            "amount": "3298",
            "cosigner": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4b",
            "model": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4c",
            "creator": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4d",
            "oracle": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea43",
            "borrower": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4f",
            "salt": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91eagb",
            "loanData": "b'Nqf\\xef\\x19\\xdbC\\x07\\xbbb\\xe1\\x1c\\xcd\\xac\\xf8U=\\x18\\xf1\\xd5\\xd4\\xdf\\xc5\\x1f'",
            "canceled": true,
            "created": "505026943.0",
            "commits": [
                {
                    "opcode": "asd",
                    "timestamp": 172811475,
                    "order": 4,
                    "proof": "0xa3d0b893d062e7286ba502c28537b9c939af867427f34673c8b94570da91ea4b",
                    "data": {
                        "value": "pepito"
                    }
                }
            ]
    }
}
```

#### 404

```json
{
    "title": "Request does not exists",
    "description": "Request with id=x does not exists"
}
```


## Fetching oracle history

    GET /v4/oracle_history/

### Query parameters:

| Field     | Type    | Description                       | Optional |
|-----------|---------|-----------------------------------|----------|
| page_size | integer | Get a list of config with n items | Yes      |
| page      | integer | Get the nth page of configs       | Yes      |


### Response

#### 200

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


## Fetching a oracle history

    GET /v4/oracle_history/:id

#### 200

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

#### 404

```json
{
    "title": "History does not exists",
    "description": "History with id=x does not exists"
}
```
