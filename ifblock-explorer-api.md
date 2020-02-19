# IFBlock Explorer API

## Introduction

[ifblock.io](https://ifblock.io) is an Explorer for BTC, BCH, BSV, and LTC blockchains, Which is build for wallets and DApp developers. These document help using IFBlock APIs to query Blocks, Transactions and UTXO \(Unspent Transaction Out\) of above coins.

## Auth Limit

Before you go on, Please let me know.

mail to `admin@ifwallet.com`

Tell us about:

* Who you are \(Personal or Organization\)
* What project you use API to do
* API call times require

All APIs has request limitation, If we found that someone is abusing the resource, we will suspend it quickly.

## API URL

The IFBlock API base URL \(refer as `{{ url }}` \) is defined as follows, every API request should starts with base URL.

```text
https://bsvapi.ifwallet.com:8221    // BSV
https://bchapi.ifwallet.com:8222    // BCH
https://btcapi.ifwallet.com:8223    // BTC
https://ltcapi.ifwallet.com:8224    // LTC
https://fchapi.ifwallet.com:8225    // FCH
```

## Block

### Get Block list

Query recently block list order by height descending.

```text
GET {{url}}/api/block/list/?page=1&limit=50
```

#### params:

**page**  _**integer**_  The page index, must greater than 1, e.g 5

**limit** _**Integer**_  Page cap limit, e.g 50

page cap is limit to 100 as default.

#### Response:

```text
{
	"code": 0,
	"data": {
		"count": 50,
		"curr_page": 1,
		"data": [{
				"bits": 486604799,
				"block_hash": "0000000099864101cbef4e8f59125e795e6c534eb80cc13977e7fafcb172607d",
				"confirmations": 1301183,
				"height": 4130,
				"merkle_root": "0f3a232b776b8aea1c3e463dba640bbaa8aa1463b41cf896f79a2bc96ebd8120",
				"miner": "",
				"next_block_hash": "000000003b75e1dcba523bc164dfd072ef527ad0858f9277cbfb65ba293bd69f",
				"nonce": 3673345280,
				"prev_block_hash": "0000000015779bf29d8aa969542938aaf6661c37449e35d4435fe98dd8c032f5",
				"reward": 5000000000,
				"size": 16786,
				"time": 1338084348,
				"tx_count": 87,
				"version": 1,
				"version_hex": "00000001"
			},
			// ...
			{
				"bits": 486604799,
				"block_hash": "000000009d9416534b3ea4f9ed9d8ff490bf409349f865147305638d9f430e45",
				"confirmations": 1301192,
				"height": 4121,
				"merkle_root": "0c303401116e7ddee22447b0883851f70065e09913294c8375ddf3ba3eb33f9d",
				"miner": "",
				"next_block_hash": "0000000022265a4d7688446b26768956d75483009cb74264f54f4ce478cf6360",
				"nonce": 1724681219,
				"prev_block_hash": "000000000231aa29fd1b409d286e105738f902751970c11e4472f29d69432cd4",
				"reward": 5000000000,
				"size": 29269,
				"time": 1338073539,
				"tx_count": 152,
				"version": 1,
				"version_hex": "00000001"
			}
		],
		"has_next": true,
		"total": 4131,
		"total_page": 83
	},
	"message": "OK"
}
```

### Get Block Detail

Query block detail by block hash.

```text
GET {{url}}/api/block/{{block_hash}}/
```

#### Params:

**block\_hash** _**String**_  Hash of a block

#### Response:

```text
{
    "code": 0,
    "data": {
        "bits": 486604799,
        "block_hash": "00000000910bdd3e130b761c8e2fdfd49838466bc81a8c673f3dc86ea8975c03",
        "confirmations": 1302705,
        "height": 4115,
        "merkle_root": "ec737459aab64ba41e34fabef3e13ef8e26b0c4dcce52225d4650ef098092728",
        "miner": "",
        "next_block_hash": "00000000e68a9564f701b48f91d2d482fe4337d053a8febbef68a6c7eb927149",
        "nonce": 502890040,
        "prev_block_hash": "00000000eb7dab76c4ab489beff92a75bdcce45d0159181450287ae0bbdfa412",
        "reward": 5000000000,
        "size": 19467,
        "time": 1338066333,
        "tx_count": 101,
        "version": 1,
        "version_hex": "00000001"
    },
    "message": "OK"
}
```

## Transaction

### Get Transaction Detail

Query transaction details by `txid`

```text
GET {{url}}/api/tx/{{txid}}/
```

#### Params:

**txid** _**String**_ Transaction ID

#### Response:

```text
{
    "code": 0,
    "data": {
        "block_hash": "000000000933ea01ad0ee984209779baaec3ced90fa3f408719526f8d77f4943",
        "confirmations": 0,
        "fee": 0,
        "height": 0,
        "in_value": 5000000000,
        "lock_time": 0,
        "out_value": 5000000000,
        "size": 204,
        "time": 0,
        "txid": "4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b",
        "version": 1,
        "vin": [
            {
                "addrs": [],
                "coinbase": "04ffff001d0104455468652054696d65732030332f4a616e2f32303039204368616e63656c6c6f72206f6e206272696e6b206f66207365636f6e64206261696c6f757420666f722062616e6b73",
                "from_txid": null,
                "from_vout": 0,
                "index": 0,
                "script": null,
                "script_hex": null,
                "type": "coinbase",
                "value": 0
            }
        ],
        "vout": [
            {
                "addrs": [
                    "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa"
                ],
                "index": 0,
                "script": "04678afdb0fe5548271967f1a67130b7105cd6a828e03909a67962e0ea1f61deb649f6bc3f4cef38c4f35504e51ec112de5c384df7ba0b8d578a4c702b6bf11d5f OP_CHECKSIG",
                "script_hex": "4104678afdb0fe5548271967f1a67130b7105cd6a828e03909a67962e0ea1f61deb649f6bc3f4cef38c4f35504e51ec112de5c384df7ba0b8d578a4c702b6bf11d5fac",
                "type": "pubkey",
                "value": 5000000000
            }
        ]
    },
    "message": "OK"
}
```

## UTXOs

### Get Addresses UTXOs

Query UTXOs of addresses list.

```text
GET {{url}}/api/address/utxo/list/
```

#### Params Data:

Params data must pass by an \`Application/json\` way instead of params in query string.

**addresses** _**List&lt;String&gt;**_ **** A List of address

**confirmations** _**Integer**_  Require confirmations

#### Response:

```text
{
    "code": 0,
    "data": [
        {
            "addr": "mnyPpMooWiBMCGqg49qguKXzHv4yg1eP4r",
            "txid": "3aac2f8454bb928214f3c1833b8da6b1b346bd75de7eb07a55252109e5ab5982",
            "value": 5000000000,
            "vout": 0
        },
        {
            "addr": "mt2AzeCorSf7yFckj19HFiXJgh9aNyc4h3",
            "txid": "ed7ab34b06e47685bdea7a32a441d874c2d3ad1893a47ddb668b5f299428588d",
            "value": 17200000000,
            "vout": 0
        },
        {
            "addr": "mt2AzeCorSf7yFckj19HFiXJgh9aNyc4h3",
            "txid": "5156c22103e9491db447959d20be6710d5ad7a6c86110b052189c5dbaab268b3",
            "value": 17200000000,
            "vout": 0
        },
        {
            "addr": "mt2AzeCorSf7yFckj19HFiXJgh9aNyc4h3",
            "txid": "c207b9acb705f08ba76805831f670b0b3ffe997f3bdcf1476e7ccc46189cd689",
            "value": 17200000000,
            "vout": 0
        }
    ],
    "message": "OK"
}
```

## Address

### Get Address Summary

Query Address Balance and summary.

```text
GET {{url}}/api/address/{{address}}/
```

#### Params:

**address** _**String**_  ****The address you want to query

#### Response:

```text
{
    "code": 0,
    "data": {
        "balance": 18627600000000,
        "cash_address": "bchtest:qzyjstrwpxrrhvy9u6pz64cxvnwluha92cqx0r0quz", // only in BCH and BSV
        "legacy_address": "mt2AzeCorSf7yFckj19HFiXJgh9aNyc4h3",
        "total_in": 71517600000000,
        "total_out": 52890000000000,
        "tx_count": 4158
    },
    "message": "OK"
}
```



### Get Addresses Transactions

Query Addresses Transactions, which will return all records of appointed addresses.

```text
GET {{url}}/api/tx/of/address/?page=1&limit=50
```

#### Params:

Params are pass by query string.

**page** _**Integer**_ **** The page num e.g 1

**limit** _**Integer**_  Page cap limit e.g 50

page cap limit to 100 as max

#### Params Data:

Params data must pass by an \`Application/json\` way instead of params in query string.

**addresses** _**List&lt;String&gt;**_  The list of addresses

#### Response:

```text
{
    "code": 0,
    "data": {
        "count": 100,
        "curr_page": 1,
        "data": [
            {
                "block_hash": "deff21ef78e9e3630ba6c30e2e2f3ae8810f5b0f5923c4143211174b400f391f",
                "confirmations": 1100254,
                "fee": 0,
                "height": 10000,
                "in_value": 5000000000,
                "index": 0,
                "lock_time": 0,
                "more_detail": false,
                "out_value": 5000000000,
                "size": "103",
                "time": 1487881889,
                "txid": "839c1510d2e4b1e6f9e1b072c58200338154866461da206984392140e82e2120",
                "v_size": 103,
                "version": 1,
                "vin": [
                    {
                        "addrs": [],
                        "coinbase": "0210270658af46a1100100000000e5b40000",
                        "from_txid": null,
                        "from_vout": 0,
                        "index": 0,
                        "script": null,
                        "script_hex": null,
                        "txin_witness": [],
                        "type": "coinbase",
                        "value": 0
                    }
                ],
                "vout": [
                    {
                        "addrs": [
                            "ms4u4DsgfqdP85ceodZkHm1TFn43tEHaiX"
                        ],
                        "index": 0,
                        "script": "OP_DUP OP_HASH160 7eb3fdb623776fb500cdb70816cf2a5256eb358e OP_EQUALVERIFY OP_CHECKSIG",
                        "script_hex": "76a9147eb3fdb623776fb500cdb70816cf2a5256eb358e88ac",
                        "type": "pubkeyhash",
                        "value": 5000000000
                    }
                ],
                "weight": 412
            },
            // ...
            {
                "block_hash": "38370bc40523489bde001108f67903ca2ce3f9fb838f17eefb253614cd907f50",
                "confirmations": 1100255,
                "fee": 0,
                "height": 9999,
                "in_value": 5000000000,
                "index": 0,
                "lock_time": 0,
                "more_detail": false,
                "out_value": 5000000000,
                "size": "103",
                "time": 1487881854,
                "txid": "d720e543b6f0317f95f8b1511af5c86a606773c6326889763ca4cf66d20405dc",
                "v_size": 103,
                "version": 1,
                "vin": [
                    {
                        "addrs": [],
                        "coinbase": "020f270658af467e100100000000e1b40000",
                        "from_txid": null,
                        "from_vout": 0,
                        "index": 0,
                        "script": null,
                        "script_hex": null,
                        "txin_witness": [],
                        "type": "coinbase",
                        "value": 0
                    }
                ],
                "vout": [
                    {
                        "addrs": [
                            "ms4u4DsgfqdP85ceodZkHm1TFn43tEHaiX"
                        ],
                        "index": 0,
                        "script": "OP_DUP OP_HASH160 7eb3fdb623776fb500cdb70816cf2a5256eb358e OP_EQUALVERIFY OP_CHECKSIG",
                        "script_hex": "76a9147eb3fdb623776fb500cdb70816cf2a5256eb358e88ac",
                        "type": "pubkeyhash",
                        "value": 5000000000
                    }
                ],
                "weight": 412
            }
        ],
        "has_next": true,
        "total": 7985,
        "total_page": 80
    },
    "message": "OK"
}
```

### Send Transaction

Broadcast transaction to blockchain.

```text
POST {{url}}/api/tool/tx/broadcast/
```

#### Params Data:

Params data must pass by an \`Application/json\` way instead of params in query string.

**raw\_tx** _**String**_  The transaction raw hex string

#### Response:

```text
{
    "code": 0,
    "data": {
        "txid": "xxxxxx"
    },
    "message": "OK"
}
```

