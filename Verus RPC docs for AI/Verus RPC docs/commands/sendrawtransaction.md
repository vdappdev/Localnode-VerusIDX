./verus help sendrawtransaction

sendrawtransaction "hexstring" ( allowhighfees )

Submits raw transaction (serialized, hex-encoded) to local node and network.

Also see createrawtransaction and signrawtransaction calls.

Arguments:
1. "hexstring"    (string, required) The hex string of the raw transaction)
2. allowhighfees    (boolean, optional, default=false) Allow high fees

Result:
"hex"             (string) The transaction hash in hex

Examples:

Create a transaction
> verus createrawtransaction "[{"txid" : "mytxid","vout":0}]" "{"myaddress":0.01}"
Sign the transaction, and get back the hex
> verus signrawtransaction "myhex"

Send the transaction (signed hex)
> verus sendrawtransaction "signedhex"

As a json rpc call
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "sendrawtransaction", "params": ["signedhex"] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/