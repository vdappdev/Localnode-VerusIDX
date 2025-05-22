takeoffer help command followed by examples with outputs:

notes:
- takeoffer uses the offer's txid as part of the inputs; the way to retrieve the relevant txid is using the getoffers command to get the txid from the result/output of getoffers.
- there are 4 possible type of takeoffer:  accept ID & deliver ID, accept ID & deliver currency, accept currency & deliver ID, accept currency & deliver currency



./verus help takeoffer

takeoffer fromaddress '{"txid":"txid" | "tx":"hextx", "changeaddress":"transparentoriaddress", "deliver":"fullidnameoriaddresstodeliver" | {"currency":"currencynameorid","amount":n}, "accept":{"address":"addressorid","currency":"currencynameorid","amount":n} | {identitydefinition} | {"txout":{"serializedtxout"}}}' (returntx) (feeamount)

If the current wallet can afford the swap, this accepts a swap offer on the blockchain, creates a transaction
to execute it, and posts the transaction to the blockchain.

Arguments
"fromaddress"            (string, required) The Sapling, VerusID, or wildcard address to send funds from, including fees for ID swaps.
                                              "*", "R*", or "i*" are valid wildcards
{
"txid"               (string, required) The transaction ID for the offer to accept
"tx"                 (string, required) The hex transaction to complete in order to accept the offer
"deliver"            (object, required) One of "fullidnameoriaddresstotrade" or {"currency":"currencynameorid", "amount":value}
"accept"             (object, required) One of {"address":"addressorid","currency":"currencynameorid","amount"} or {identitydefinition}
"feeamount"          (number, optional) Specific fee amount requested instead of default miner's fee
}

Result:
   "txid" : "transactionid" (string) The transaction id if (returntx) is false
   "hextx" : "hex"         (string) The hexadecimal, serialized transaction if (returntx) is true

Examples:
> verus takeoffer fromaddress '{"txid":"txid" | "tx":"hextx", "deliver":"fullidnameoriaddresstodeliver" | {"currency":"currencynameorid","amount":...}, "accept":{"address":"addressorid","currency":"currencynameorid","amount"} | {identitydefinition}}' (returntx) (feeamount)
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "takeoffer", "params": [fromaddress {"txid":"txid" | "tx":"hextx", "deliver":"fullidnameoriaddresstodeliver" | {"currency":"currencynameorid","amount":...}, "accept":{"address":"addressorid","currency":"currencynameorid","amount"} | {identitydefinition}} (returntx) (feeamount)] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/




takeoffer EXAMPLES & OUTPUTS/RESULTS:



takeoffer EXAMPLE accept ID & deliver ID:

./verus takeoffer "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss" '{"txid": "89f724fc8b19bd83bf97834ca66b368dc969dc1824117cb54a9f210b58884c82", "changeaddress":"RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss", "deliver":"user49@", "accept":{"name": "user55@", "parent": "vrsctest", "primaryaddresses": ["RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"], "minimumsignatures": 1}}' "" "0.0001"

{
  "txid": "8ab1cd881e2caf0103b63830e901ae88048aad277246206a193f9e79bee6774b"
}



takeoffer EXAMPLE accept ID & deliver currency:

./verus takeoffer "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss" '{"txid":"b4edc618356fa7a5f2288a4b06ecd7c407c4c6dd7c9d1841bf5c0a970b24acd0", "changeaddress":"RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss", "deliver":{"currency":"vrsctest", "amount":111}, "accept":{"name": "Dev7", "parent": "vrsctest", "primaryaddresses": ["RGi75h173LD84tTThCu73B9Dp6rupM5zoz"], "minimumsignatures": 1, "revocationauthority": "dev28@", "recoveryauthority": "dev28@", "privateaddress":"zs1kv5zk4kyjuyknqmh6neyand9uewp9h5k0fayxjxah5mmk564d4yxxfqtwwd6atytlrhvyy3dj04"}}' "" "0.0001"

{
  "txid": "6e0af4061ef2bf7f5e9c93d5180ed06a7d8fc91801fd03527c64c60fd1a0f346"
}



takeoffer EXAMPLE accept currency & deliver ID:


./verus takeoffer "dev28@" '{"txid":"0997139ge5edf8c1b2165tk2e618e3fced5102ad1f6109fb5afab651e9d25byi", "changeaddress":"user55@", "deliver":"sendit@", "accept":{"address":"RGi75h173LD84tTThCu73B9Dp6rupM5zoz","currency":"vrsc","amount":175}}'

{
  "txid": "8e0vn4091eh2bf7f5e9c93d5180ed06a5d8gc91801fd03497c64c60sd1a0j398"
}




takeoffer EXAMPLE accept currency & deliver currency:


./verus takeoffer "dev7@" '{"txid":"0591139de5ecf6c1b1165ef2e618e5fced5102ad1f6109fb5afab651e9d25bae", "changeaddress":"dev7@", "deliver":{"currency":"dai.veth","amount":1000}, "accept":{"address":"dev7@","currency":"vrsc","amount":100}}'

{
  "txid": "8e0vn4091eh2bf7f5e9c93d5180ed06a5d8gc91801fd03497c64c60sd1a0j398"
}