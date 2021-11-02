# Table of contents
* [Base URL](#base-url)
* [Endpoint types](#endpoint-types)
* [Constructing the request](#constructing-the-request)
* [API documentation](#api-documentation)
* [Error codes](#error-codes)
# Base URL
* The base URL is: https://rs-wallet-dev.bbtserv.com/
# Endpoint types
### Secure endpoints
All secure endpoints require [authentication](#constructing-the-request) and use the method GET.

* [GET /api/token/mint-history](#get-apiminthistory)
* [GET /api/token/burn-history](#get-apiburnhistory)
* [GET /api/token/transfer-history](#get-apitransferhistory)
* [GET /api/token/balance](#get-apibalance)
* [GET /api/tx-status](#get-apitx-status)

All secure endpoints require [authentication](#constructing-the-request) and use the method POST.
* [POST /api/token/mint](#get-apimint)
* [POST /api/token/burn](#get-apiburn)
* [POST /api/token/transfer](#get-apitransfer)
* [POST /api/token/add-blacklist](#get-apiaddblacklist)
* [POST /api/token/revoke-blacklist](#get-apirevokeblacklist)
* [POST /api/token/set-owner](#get-apisetowner)
* [POST /api/token/set-router](#get-apisetowner)
* [POST /api/hot/transfer](#get-apitransfer)
* [POST /api/hot/set-owner](#get-apisetowner)
* [POST /api/router/transfer](#get-apitransfer)
* [POST /api/router/set-hotwallet](#get-apisethotwallet)
* [POST /api/router/set-owner](#get-apisetowner)
* [POST /api/router/set-symboltoken](#get-apisetsymboltoken)


# Constructing the request
### Request headers (GET, POST)
Authentication requires API KEY. Every request to the server must contain the following in the request header:
* X-RS-APIKEY: {API KEY}
# API documentation
Refer to the following for description of each endpoint
### GET /api/token/mint-history
#### Description:
List mint history
#### Query(URL):
* `addr`		**string**		the address (optional)
#### Example:
?addr=0x25146786e7378f91506793a28F8814f76c3943c8
### Response
```
{
    "error": 0,
    "result": [
        {
            "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
            "to": "0x76058D4a05054396Bca88A003B06Ae745f9C4b9C",
            "amount": 100,
            "currency": "POP",
            "time": "Sun Aug 29 2021 22:59:04",
            "bkc_url": "https://testnet.bkcscan.com/tx/0x0da92773f156cd152c207edc05c15878dd45f5d01513585728d377dd0be0e842/token-transfers"
        }
        ...
    ]
}
```
### GET /api/token/burn-history
#### Description:
List burn history
#### Query(URL):
* `addr`		**string**		The address (optional)

#### Example:
?addr=0x25146786e7378f91506793a28F8814f76c3943c8
### Response:
```
{
    "error": 0,
    "result": [
        {
            "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
            "addr": "0x75e7D74FB1517b01665Cb84F07b4F14b5F2032db",
            "amount": 50,
            "currency": "POP",
            "time": "Mon Aug 30 2021 14:24:20",
            "bkc_url": "https://testnet.bkcscan.com/tx/0xdd911227d1a0a7dd64d2afaa3004ba05123fbe71648ce60e7be66e1e95593d5a/token-transfers"
        }
    ]
}
```
### GET /api/token/transfer-history
#### Description:
List transfer history
#### Query(URL):
* `addr`		**string**		The address (optional)
#### Example:
?addr=0x25146786e7378f91506793a28F8814f76c3943c8
### Response:
```
{
    "error": 0,
    "result": [
        {
            "from": "0xA82aF6A7A06c7518C30cdf965ABe043b028FD22c",
            "to": "0x76058D4a05054396Bca88A003B06Ae745f9C4b9C",
            "amount": 10,
            "currency": "POP",
            "time": "Sun Aug 29 2021 23:27:06"
        },
        ...
    ]
}
```
### GET /api/token/balance
#### Description:
check balance
#### Query(URL):
* `addr`		**string**		The address (require)
#### Example:
?addr=0x25146786e7378f91506793a28F8814f76c3943c8
### Response
```
{
    "error": 0,
    "result": {
        "balance": 120,
        "currency": "POP"
    }
}
```
### GET /api/tx-status
#### Description:
check transaction status
#### Query(URL):
* `tx-hash`		**string**		The transaction hash (require)
#### Example:
?tx-hash=0x5a049827e49c8ad38a50a8007d054d25b69ba9440b0c81d0774a9212d44ef221
### Response
```
{
    "error": 0,
    "result": "success"
}
```
### POST /api/token/mint
#### Description:
mint token
#### Body:
* `to`		**string**		to address (require)
* `amount`		**number**		amount token (require)
#### Example:
```
{
    "to":"0xA82aF6A7A06c7518C30cdf965ABe043b028FD22c",
    "amount":1000
}
```
### Response:
```
{
    "error": 0,
    "result": {
        "method": "mint",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "to": "0xA82aF6A7A06c7518C30cdf965ABe043b028FD22c",
        "amount": 1000,
        "currency": "POP",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/token/mint",
        "time": "Wed Sep 01 2021 17:47:19",
        "transaction_hash": "0x85c9d2cc48c885f340baaf7dfb3dd3dd49a2a79a42077f40fd025d680b25ee4d",
        "block_hash": "0xfd602879b0119dbe22a67c72cab62b76d93b2c26bfdf1f295beb963808f33696",
        "gas_used": 39735,
        "gas_fee": 0.00198675,
        "bkc_url": "https://testnet.bkcscan.com/tx/0x85c9d2cc48c885f340baaf7dfb3dd3dd49a2a79a42077f40fd025d680b25ee4d/token-transfers"
    }
}
```
### POST /api/token/burn
#### Description:
burn token
#### Body:
* `addr`		**string**		to address (require)
* `amount`		**number**		amount token (require)
#### Example:
```
{
    "addr":"0xA82aF6A7A06c7518C30cdf965ABe043b028FD22c",
    "amount":500
}
```
### Response
```
{
    "error": 0,
    "result": {
        "method": "burn",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "addr": "0xA82aF6A7A06c7518C30cdf965ABe043b028FD22c",
        "amount": 500,
        "currency": "POP",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/token/burn",
        "time": "Wed Sep 01 2021 17:49:25",
        "transaction_hash": "0x2e008f924e55751086e1266b5e38f82e8c84a5a4dcf2d516196e875f31441e6f",
        "block_hash": "0x83cab4330dfbb63789bb41385373a2e92ddc5aecf6b72343340a268bc0ccdba8",
        "gas_used": 38160,
        "gas_fee": 0.001908,
        "bkc_url": "https://testnet.bkcscan.com/tx/0x2e008f924e55751086e1266b5e38f82e8c84a5a4dcf2d516196e875f31441e6f/token-transfers"
    }
}
```
### POST /api/token/transfer
#### Description:
transfer token 
#### Body:
* `from`		**string**		from address (require)
* `to`		**string**		to address (require)
* `amount`		**number**		amount token (require)
#### Example:
```
{
    "from":"0x2E89c9a359f846454D23C2EC692ce314815d5C2a",
    "to":"0x76058D4a05054396Bca88A003B06Ae745f9C4b9C",
    "amount":100
}
```
### Response:
```
{
    "error": 0,
    "result": {
        "method": "transfer",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "from": "0x162B01ABe4739BA1F6Fa9911eB92f0Cbe6154078",
        "to": "0x76058D4a05054396Bca88A003B06Ae745f9C4b9C",
        "amount": 100,
        "currency": "POP",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/token/transfer",
        "time": "Wed Sep 01 2021 17:51:24",
        "transaction_hash": "0x66145045a18b573661286e85d598ffaab722b6b6ae241fac0e204cd010f35826",
        "block_hash": "0x3df6792cbed149e4de202e9d3b638296d80beb480a71f25395a3c48520829e05",
        "gas_used": 44176,
        "gas_fee": 0.0022088,
        "bkc_url": "https://testnet.bkcscan.com/tx/0x66145045a18b573661286e85d598ffaab722b6b6ae241fac0e204cd010f35826/token-transfers"
    }
}
```

### POST /api/token/add-blacklist
#### Description:
add address blacklist
#### Body:
* `addr`		**string**		to address (require)
#### Example:
```
{
    "addr":"0x76058D4a05054396Bca88A003B06Ae745f9C4b9C"
}
```
### Response
```
{
    "error": 0,
    "result": {
        "method": "add-blacklist",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "addr": "0x76058D4a05054396Bca88A003B06Ae745f9C4b9C",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/token/add-blacklist",
        "time": "Wed Sep 01 2021 17:53:17",
        "transaction_hash": "0x85fdcf830de7895e39abca3258fbbecc8698215f7330bca6cd45e448dd30b1dd",
        "block_hash": "0x61a68e6811e53390d37bffa5d2c61557cb20099ff4ad6b1bbf26533430dd204d",
        "gas_used": 43484,
        "gas_fee": 0.0021742,
        "bkc_url": "https://testnet.bkcscan.com/tx/0x85fdcf830de7895e39abca3258fbbecc8698215f7330bca6cd45e448dd30b1dd/nternal-transactions"
    }
}
```
### POST /api/token/revoke-blacklist
#### Description:
revoke address blacklist
#### Body:
* `addr`		**string**		to address (require)
#### Example:
```
{
    "addr":"0x76058D4a05054396Bca88A003B06Ae745f9C4b9C"
}
```
### Response
```
{
    "error": 0,
    "result": {
        "method": "revoke-blacklist",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "addr": "0x76058D4a05054396Bca88A003B06Ae745f9C4b9C",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/token/revoke-blacklist",
        "time": "Wed Sep 01 2021 17:54:37",
        "transaction_hash": "0xc839dc387166043acc1a6300d3ded9b61b2abd9c8e045b65085770a489310f72",
        "block_hash": "0x6153f1d0b835b8d10b9f7aae0d74e8c8a03abd7ce01d505dd1bfe10a49298eec",
        "gas_used": 14239,
        "gas_fee": 0.00071195,
        "bkc_url": "https://testnet.bkcscan.com/tx/0xc839dc387166043acc1a6300d3ded9b61b2abd9c8e045b65085770a489310f72/nternal-transactions"
    }
}
```
### POST /api/token/set-owner
#### Description:
token set owner
#### Query:
* `newowner`		**string**		new owner address (require)
#### Example:
```
{
    "newowner":"0x25146786e7378f91506793a28F8814f76c3943c8"
}
```
### Response
```
{
    "error": 0,
    "result": {
        "method": "token-set-owner",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "newowner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/token/set-owner",
        "time": "Wed Sep 01 2021 18:27:23",
        "transaction_hash": "0xa695fae2877ed992b3d94b134fa3cf3e3137cf0f8da568eaee6e2e6caa314158",
        "block_hash": "0x3272d1082e2d9ba2679241e13a9708fbd048db153f947b634132055b285327d9",
        "gas_used": 24300,
        "gas_fee": 0.001215,
        "bkc_url": "https://testnet.bkcscan.com/tx/0xa695fae2877ed992b3d94b134fa3cf3e3137cf0f8da568eaee6e2e6caa314158/internal-transactions"
    }
}
```
### POST /api/token/set-router
#### Description:
token set router
#### Query:
* `router`		**string**		router contract address (require)
#### Example:
```
{
    "router":"0x3B65Aba64a7188397603dc02F8559D9Da11Dd7F8"
}
```
### Response
```
{
    "error": 0,
    "result": {
        "method": "token-set-router",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "router": "0x3B65Aba64a7188397603dc02F8559D9Da11Dd7F8",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/token/set-router",
        "time": "Wed Sep 01 2021 17:59:38",
        "transaction_hash": "0xe67a148b32c05ce38507f20e1fcc73933950ab2b916a273ec6de518e3d24e5ad",
        "block_hash": "0xe224244bb3a3eb0dedad4e04967872f863fc10771bf60fb365467e098bd1af0d",
        "gas_used": 24320,
        "gas_fee": 0.001216,
        "bkc_url": "https://testnet.bkcscan.com/tx/0xe67a148b32c05ce38507f20e1fcc73933950ab2b916a273ec6de518e3d24e5ad/internal-transactions"
    }
}
```
### POST /api/hot/transfer
#### Description:
hot wallet transfer
#### Query:
* `to`		**string**		to address (require)
* `amount`		**number**		amount token (require)
#### Example:
```
{
    "to":"0x76058D4a05054396Bca88A003B06Ae745f9C4b9C",
    "amount":100
}
```
### Response
```
{
    "error": 0,
    "result": {
        "method": "transfer",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "from": "0x162B01ABe4739BA1F6Fa9911eB92f0Cbe6154078",
        "to": "0x76058D4a05054396Bca88A003B06Ae745f9C4b9C",
        "amount": 100,
        "currency": "POP",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/hot/transfer",
        "time": "Wed Sep 01 2021 18:01:51",
        "transaction_hash": "0xf970448450151445e115bdda6e7a517cf2fe93af36c08939c8f4d68134ba5487",
        "block_hash": "0x20b4270e8d5f63edf8cbe192a8e3b20f78536d26c8968c3b0212c6f86c864490",
        "gas_used": 44176,
        "gas_fee": 0.0022088,
        "bkc_url": "https://testnet.bkcscan.com/tx/0xf970448450151445e115bdda6e7a517cf2fe93af36c08939c8f4d68134ba5487/token-transfers"
    }
}
```
### POST /api/hot/set-owner
#### Description:
hot set owner
#### Query:
* `newowner`		**string**	  new owner address (require)
#### Example:
```
{
    "newowner":"0x25146786e7378f91506793a28F8814f76c3943c8"
}
```
### Response
```
{
    "error": 0,
    "result": {
        "method": "hot-set-owner",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "newowner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/hot/set-owner",
        "time": "Wed Sep 01 2021 18:05:07",
        "transaction_hash": "0x82d321455240c031f542c6a96e0800ab3b177b94e2fa31a9180fc50ad4fc30ad",
        "block_hash": "0xdab313e180a17e98eba61667a3070df5dfa14abdf45e78f8fa9d62a46dea307e",
        "gas_used": 24208,
        "gas_fee": 0.0012104,
        "bkc_url": "https://testnet.bkcscan.com/tx/0x82d321455240c031f542c6a96e0800ab3b177b94e2fa31a9180fc50ad4fc30ad/internal-transactions"
    }
}
```
### POST /api/router/transfer
#### Description:
router transfer
#### Query:
* `from`		**string**		from address (require)
* `to`		**string**		to address (require)
* `fee`		**number**		fee (require)
* `amount`		**number**		amount (require)
#### Example:
```
{
    "from":"0xA82aF6A7A06c7518C30cdf965ABe043b028FD22c",
    "to":"0x76058D4a05054396Bca88A003B06Ae745f9C4b9C",
    "fee": 10,
    "amount":100
}
```
### Response
```
{
    "error": 0,
    "result": [
        {
            "method": "transfer",
            "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
            "from": "0xA82aF6A7A06c7518C30cdf965ABe043b028FD22c",
            "to": "0x76058D4a05054396Bca88A003B06Ae745f9C4b9C",
            "amount": 100,
            "currency": "POP",
            "user_agent": "PostmanRuntime/7.28.3",
            "req_method": "POST",
            "url_path": "/api/router/transfer",
            "time": "Wed Sep 01 2021 18:06:51",
            "transaction_hash": "0x2804d2601f2851ec7232b82713109c5f64b79209c98dd6e490c2bb3ef26c76d8",
            "block_hash": "0xa4fe97eac4bef49d01fcdb3868342663c1b8539eb9d4ecde83c90edbeb14198c",
            "gas_used": 59906,
            "gas_fee": 0.0029953,
            "bkc_url": "https://testnet.bkcscan.com/tx/0x2804d2601f2851ec7232b82713109c5f64b79209c98dd6e490c2bb3ef26c76d8/token-transfers"
        },
        {
            "method": "transfer",
            "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
            "from": "0xA82aF6A7A06c7518C30cdf965ABe043b028FD22c",
            "to": "0x162B01ABe4739BA1F6Fa9911eB92f0Cbe6154078",
            "amount": 10,
            "currency": "POP",
            "user_agent": "PostmanRuntime/7.28.3",
            "req_method": "POST",
            "url_path": "/api/router/transfer",
            "time": "Wed Sep 01 2021 18:06:51",
            "transaction_hash": "0x2804d2601f2851ec7232b82713109c5f64b79209c98dd6e490c2bb3ef26c76d8",
            "block_hash": "0xa4fe97eac4bef49d01fcdb3868342663c1b8539eb9d4ecde83c90edbeb14198c",
            "gas_used": 59906,
            "gas_fee": 0.0029953,
            "bkc_url": "https://testnet.bkcscan.com/tx/0x2804d2601f2851ec7232b82713109c5f64b79209c98dd6e490c2bb3ef26c76d8/token-transfers"
        }
    ]
}
```
### POST /api/router/set-hotwallet
#### Description:
router set hotwallet
#### Query:
* `hotwallet`		**string**		hotwallet address (require)
#### Example:
```
{
    "hotwallet":"0x162B01ABe4739BA1F6Fa9911eB92f0Cbe6154078"
}
```
### Response
```
{
    "error": 0,
    "result": {
        "method": "router-set-hotwallet",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "hotwallet": "0x162B01ABe4739BA1F6Fa9911eB92f0Cbe6154078",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/router/set-hotwallet",
        "time": "Wed Sep 01 2021 18:24:34",
        "transaction_hash": "0x0338d5932f15fb076f9fd7713f5c9ae81a0d8fce79bb04e3fffc1b1e6caad676",
        "block_hash": "0xb1203fc98bf0f289c3e09e26d18b89282040f06e1188ee236adc52659ccd5dec",
        "gas_used": 28345,
        "gas_fee": 0.00141725,
        "bkc_url": "https://testnet.bkcscan.com/tx/0x0338d5932f15fb076f9fd7713f5c9ae81a0d8fce79bb04e3fffc1b1e6caad676/internal-transactions"
    }
}
```
### POST /api/router/set-owner
#### Description:
router set owner
#### Query:
* `newowner`		**string**		newowner address (require)
#### Example:
```
{
    "newowner":"0x25146786e7378f91506793a28F8814f76c3943c8"
}
```
### Response
```
{
    "error": 0,
    "result": {
        "method": "router-set-owner",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "newowner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/router/set-owner",
        "time": "Wed Sep 01 2021 18:19:07",
        "transaction_hash": "0x3687c61aa699ae8ed2710f6fc7a1526b7d9a0169a5899a3d0286739f6aebe727",
        "block_hash": "0x15b2a8c69d2ec9f9763213ec340b4fe473eb4ae474eb580df8f4063fa709f77f",
        "gas_used": 24146,
        "gas_fee": 0.0012073,
        "bkc_url": "https://testnet.bkcscan.com/tx/0x3687c61aa699ae8ed2710f6fc7a1526b7d9a0169a5899a3d0286739f6aebe727/internal-transactions"
    }
}
```

### POST /api/router/set-symboltoken
#### Description:
router set symboltoken
#### Query:
* `symboltoken`		**string**		token address (require)
#### Example:
```
{
    "symboltoken":"0x6E3973daa0E36a6Ab77C9f394fC950934D97BB7D"
}
```
### Response
```
{
    "error": 0,
    "result": {
        "method": "router-set-symboltoken",
        "owner": "0x25146786e7378f91506793a28F8814f76c3943c8",
        "symboltoken": "0x6E3973daa0E36a6Ab77C9f394fC950934D97BB7D",
        "user_agent": "PostmanRuntime/7.28.3",
        "req_method": "POST",
        "url_path": "/api/router/set-symboltoken",
        "time": "Wed Sep 01 2021 18:23:19",
        "transaction_hash": "0x16e576065195e99da8bd894f7c358cad322e43412e78fcb3b9b0ff75d771635c",
        "block_hash": "0xac1ffe3d5f334180cf6cc191491852e06ef5fd2014ad3401ae29f2e534e68250",
        "gas_used": 28367,
        "gas_fee": 0.00141835,
        "bkc_url": "https://testnet.bkcscan.com/tx/0x16e576065195e99da8bd894f7c358cad322e43412e78fcb3b9b0ff75d771635c/internal-transactions"
    }
}
```
# Error codes
Refer to the following descriptions:

Code | Description
------------ | ------------
0 | No error
1 | Invalid JSON payload
2 | Missing X-RS-APIKEY
3 | Invalid API key
4 | API pending for activation
5 | IP not allowed
6 | Missing / invalid signature
7 | Missing timestamp
8 | Invalid timestamp
9 | Invalid user
10 | Invalid parameter
11 | Invalid symbol
12 | Invalid amount
13 | Invalid rate
14 | Improper rate
15 | Amount too low
16 | Failed to get balance
17 | Wallet is empty
18 | Insufficient balance
19 | Failed to insert order into db
20 | Failed to deduct balance
21 | Invalid order for cancellation
22 | Invalid side
23 | Failed to update order status
24 | Invalid order for lookup
25 | KYC level 1 is required to proceed
30 | Limit exceeds
40 | Pending withdrawal exists
41 | Invalid currency for withdrawal
42 | Address is not in whitelist
43 | Failed to deduct crypto
44 | Failed to create withdrawal record
45 | Nonce has to be numeric
46 | Invalid nonce
47 | Withdrawal limit exceeds
48 | Invalid bank account
49 | Bank limit exceeds
50 | Pending withdrawal exists
51 | Withdrawal is under maintenance
52 | Not owner
53 | Invalid Privatekey
54 | Insufficient kub
55 | Blacklist address
56 | Over hardcap
90 | Server error (please contact support)
