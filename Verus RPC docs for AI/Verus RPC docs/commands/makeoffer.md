makeoffer help command followed by examples with outputs:

notes:
- 4 possible types of makeoffers:  ID for ID, ID for Currency, Currency for ID, Currency for Currency
- when an ID@ is in the "for" section of the makeoffer command, there are some required parameters in the identity json and some optional ones:  Required = name, parent, primaryaddresses, minimumsignatures.  Optional= privateaddress, revocationauthority, recoveryauthority. (there are other optional parameters but we'll leave those out for now - they include contentmultimap and timelock)
- the output/result includes a txid... this txid is used as an input in the takeoffer command; it can also be obtained from the output/result of the getoffers command and that would be the best way to have the workflow for ux, is by using the txid returned from getoffers.


./verus help makeoffer

makeoffer fromaddress '{"changeaddress":"transparentoriaddress", "expiryheight":blockheight, "offer":{"currency":"anycurrency", "amount":...} | {"identity":"idnameoriaddress",...}', "for":{"address":..., "currency":"anycurrency", "amount":...} | {"name":"identityforswap","parent":"parentid","primaryaddresses":["R-address(s)"],"minimumsignatures":1,...}}' (returntx) (feeamount)

This sends a transaction which provides a completely decentralized, fully on-chain an atomic swap offer for
"decentralized swapping of any blockchain asset, including any/multi currencies, NFTs, identities, contractual
"agreements and rights transfers, or to be used as bids for an on-chain auction of any blockchain asset(s).
"Sources and destination of funds for swaps can be any valid transparent address capable of holding or controlling
the specific asset.

Arguments
1. "fromaddress"             (string, required) The VerusID, or wildcard address to send funds from. "*", "R*", or "i*" are valid wildcards
2. {
     "changeaddress"         (string, required) Change destination when constructing transactions
     "expiryheight"          (number, optional) Block height at which this offer expires. Defaults to 20 blocks (avg 1/minute)
     "offer"                 (object, required) Funds description or identity name, "address" in this object should be an address of the person making an offer for change
     "for"                   (object, required) Funds description or full identity description
   }
3. "returntx"                (bool, optional) default = false, if true, returns a transaction waiting for taker completion instead of posting
4. "feeamount"               (value, optional) default = 0.0001

Result:
{
  "txid" : "transactionid", The hex transaction id on success
  "hex" : "serializedtx"   If hex is requested, hex serialization of partial transaction instead of txid is returned on success
}

Examples:
> verus makeoffer fromaddress '{"changeaddress":"transparentoriaddress", "expiryheight":blockheight, "offer":{"currency":"anycurrency", "amount":...} | {"identity":"idnameoriaddress",...}', "for":{"address":..., "currency":"anycurrency", "amount":...} | {"name":"identityforswap","parent":"parentid","primaryaddresses":["R-address(s)"],"minimumsignatures":1,...}}' (returntx) (feeamount)
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "makeoffer", "params": [fromaddress '{"changeaddress":"transparentoriaddress", "expiryheight":blockheight, "offer":{"currency":"anycurrency", "amount":...} | {"identity":"idnameoriaddress",...}', "for":{"address":..., "currency":"anycurrency", "amount":...} | {"name":"identityforswap","parent":"parentid","primaryaddresses":["R-address(s)"],"minimumsignatures":1,...}}' (returntx) (feeamount)] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/




EXAMPLES & OUTPUTS/RESULTS:



EXAMPLE offer:  id for id

with privateaddress & revoke/recover authorities:

./verus makeoffer "dev28@" '{"changeaddress":"dev28@", "expiryheight":300003, "offer":{"identity":"dev7@"}, "for":{"name":"i made this for you","parent":"iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq","primaryaddresses":["RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"],"minimumsignatures":1, "privateaddress":"zs1kv5zk4kyjuyknqmh6neyand9uewp9h5k0fayxjxah5mmk564d4yxxfqtwwd6atytlrhvyy3dj04", "revocationauthority":"dev28@", "recoveryauthority":"dev28@"}}' "" "0.0001"

{
  "txid": "9cf9ee5dc1ee6a8baae4347963567a164b28bdf34f6f2fb55cef59102c0f3592",
  "oprettxid": "0ca2345111897fa2fc5e4ff90a2d13b350d8a572f33f73ca683da02a20e30a46"
}


without privateaddress & revoke/recover authorities:

./verus makeoffer "dev28@" '{"changeaddress":"dev28@", "expiryheight":300003, "offer":{"identity":"User55@"}, "for":{"name":"User99","parent":"iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq","primaryaddresses":["RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"],"minimumsignatures":1}}' "" "0.0001"

{
  "txid": "846bbe33c48b618f07da033a2b01f1fe0d2a7968e83d145a5193a724e3e79e80",
  "oprettxid": "1909d1aaf221822db0f81c216ac59caebf3ad7ddaa1a02bbb431a1632bdfd3cf"
}



EXAMPLE offer: identity for currency


./verus makeoffer "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss" '{"changeaddress":"RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss", "expiryheight":500000, "offer":{"identity":"Dev14@"}, "for":{"address":"RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss", "currency":"vrsctest", "amount":20}}' "" "0.0001"

{
  "txid": "0accd88a2d79bcf56b3c6c0e18255130e5943e34ba57cac7f8dc32db8087d745",
  "oprettxid": "da16ecc0bab35e56e2fffdca9f8b9b6847c2441457fdc12ac646010432995d1d"
}



EXAMPLE offer: currency for identity


./verus makeoffer "RGGfvnyjF1is1jGwPKVSNSDNov6V4aBDMF" '{"changeaddress":"RGGfvnyjF1is1jGwPKVSNSDNov6V4aBDMF", "expiryheight":300000, "offer":{"currency":"vrsctest", "amount":60}, "for":{"name":"i made this for you@","parent":"iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq","primaryaddresses":["RGGfvnyjF1is1jGwPKVSNSDNov6V4aBDMF"],"minimumsignatures":1}}' "" "0.0001"

{
  "txid": "a3b07cba5bbe60a5a03d7711dbe17b0c5d2e314936e444c18e5043f7d7104a16",
  "oprettxid": "677891b9d36f338459d3a247fddd9e2d76419e259a0fc9ceb290af2bc1fc8dcf"
}




EXAMPLE offer: currency for currency


./verus makeoffer "RPtKtqx8zo0pLhw3stBwoUIKCyEeToV2g2" '{"changeaddress":"RPtKtqx8zo0pLhw3stBwoUIKCyEeToV2g2", "expiryheight":2975703, "offer":{"currency":"vrsc", "amount":60}, "for":{"address":"RPtKtqx8zo0pLhw3stBwoUIKCyEeToV2g2", "currency":"tbtc.veth", "amount":0.005}}' "" "0.0001"

{
  "txid": "47b598e6662d9c84862ff666d433caa7188800b90acee33a931515c77b669a42",
  "oprettxid": "25dba718b23e16b1463c373fef4fb3c096f8ead45ebd2c572efe83aa1afdd41a"
}


