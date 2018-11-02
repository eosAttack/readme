# using eosio.wrap to delegatebw blacklist account

## ecaf order

https://bloks.io/transaction/d082a93cc3ae1e2e6eabbb3d80c313afbfb7b9e9a91bfdbee0ab10b4f0479ded

https://eoscorearbitration.io/wp-content/uploads/2018/10/ECAF-Order-of-Emergency-Protection-2018-10-31-AO-017.pdf

## accounts in ecaf order

- refundwallet
- jhonnywalker
- alibabaioeos
- whitegroupes
- 24cryptoshop
- minedtradeos

## blacklist not work

transfer flow:

24cryptoshop -> walletfaucet -> notrealchain -> ucentralized -> irreversibls -> irreversibly -> ispersistent

create account flow:

1eooooooooos -> walletfaucet -> notrealchain -> ucentralized -> irreversibls -> irreversibly -> ispersistent

## delegatebw ispersistent to prevent further transfer

## review multisig data
```
eos multisig review dappfactory1 stakeblack
```
```json
{
  "proposal_name": "stakeblack",
  "packed_transaction": "f8aedd5b00000000000000000000010040359703ea3055000000000080545702301b9a744e83305500000000a8ed32320040359703ea305500000000a8ed32326b301b9a744e8330550000000000000000000000000000010000000000ea305500003f2a1ba6a24a0190a7cad8e1ab2a7600000000a8ed32323190a7cad8e1ab2a7690a7cad8e1ab2a7600bd01050000000004454f5300000000000000000000000004454f5300000000000000",
  "transaction": {
    "expiration": "2018-11-03T14:21:44",
    "ref_block_num": 0,
    "ref_block_prefix": 0,
    "max_net_usage_words": 0,
    "max_cpu_usage_ms": 0,
    "delay_sec": 0,
    "context_free_actions": [],
    "actions": [{
        "account": "eosio.wrap",
        "name": "exec",
        "authorization": [{
            "actor": "eoscannonchn",
            "permission": "active"
          },{
            "actor": "eosio.wrap",
            "permission": "active"
          }
        ],
        "data": {
          "executer": "eoscannonchn",
          "trx": {
            "expiration": "1970-01-01T00:00:00",
            "ref_block_num": 0,
            "ref_block_prefix": 0,
            "max_net_usage_words": 0,
            "max_cpu_usage_ms": 0,
            "delay_sec": 0,
            "context_free_actions": [],
            "actions": [{
                "account": "eosio",
                "name": "delegatebw",
                "authorization": [{
                    "actor": "ispersistent",
                    "permission": "active"
                  }
                ],
                "data": "90a7cad8e1ab2a7690a7cad8e1ab2a7600bd01050000000004454f5300000000000000000000000004454f530000000000"
              }
            ],
            "transaction_extensions": []
          }
        },
        "hex_data": "301b9a744e8330550000000000000000000000000000010000000000ea305500003f2a1ba6a24a0190a7cad8e1ab2a7600000000a8ed32323190a7cad8e1ab2a7690a7cad8e1ab2a7600bd01050000000004454f5300000000000000000000000004454f53000000000000"
      }
    ],
    "transaction_extensions": []
  }
}
```

## delegatebw transaction data

```
curl -X POST \
  http://eos.greymass.com/v1/chain/abi_bin_to_json \
  -H 'Content-Type: application/json' \
  -d '{
	"code":"eosio", 
	"action":"delegatebw", 
	"binargs":"90a7cad8e1ab2a7690a7cad8e1ab2a7600bd01050000000004454f5300000000000000000000000004454f530000000000"
	
}'
```

```json
{
    "args": {
        "from": "ispersistent",
        "receiver": "ispersistent",
        "stake_net_quantity": "8400.0000 EOS",
        "stake_cpu_quantity": "0.0000 EOS",
        "transfer": 0
    }
}
```

## no transfer just delegatebw

## multisig status

https://bloks.io/msig?proposer=dappfactory1&proposal=stakeblack