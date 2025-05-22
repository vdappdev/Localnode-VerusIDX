registernamecommitment help command followed by examples with outputs:

notes:
- registernamecommitment and registeridentity are used in the workflow to create a VerusID  
- names are not case-sensitive, and can include emojis, numbers, letters, and most symbols
- IDs can be a root ID or a sub-ID.  The root ID is child, the chain is the parent and system (example: "Pear.vrsctest@") The sub-ID is child, the currency it's defined from is parent, the chain is system (example:"Pear.kaiju.vrsctest@" aka "Pear.kaiju@")
- the command's output/result is used as part of the "registeridentity" command to complete the process of registering an ID.


./verus help registernamecommitment

registernamecommitment "name" "controladdress" ("referralidentity") ("parentnameorid") ("sourceoffunds")

Registers a name commitment, which is required as a source for the name to be used when registering an identity. The name commitment hides the name itself
while ensuring that the miner who mines in the registration cannot front-run the name unless they have also registered a name commitment for the same name or
are willing to forfeit the offer of payment for the chance that a commitment made now will allow them to register the name in the future.

Names must not have leading, trailing, or multiple consecutive spaces and must not include any of the following characters between parentheses (\/:*?"<>|@)

Arguments
"name"                           (string, required)  the unique name to commit to. creating a name commitment is not a registration, and if one is created for a name that exists, it may succeed, but will never be able to be used.
"controladdress"                 (address, required) address that will control this commitment. IMPORTANT: this is not necessarily the address that should control the actual ID, and it should be present in the current wallet that is registering the ID. Change may go to this address.
"referralidentity"               (identity, optional)friendly name or identity address that is provided as a referral mechanism and to lower network cost of the ID
"parentnameorid-pbaasonly"       (currency, optional)friendly name or currency i-address, which will be the parent of this ID and dictate issuance rules & pricing
"sourceoffunds"                  (addressorid, optional) optional address to use for source of funds. if not specified, transparent wildcard "*" is used


Result: obj
{
    "txid" : "hexid"
    "namereservation" :
    {
        "name"    : "namestr",     (string) the unique name in this commitment
        "salt"    : "hexstr",      (hex)    salt used to hide the commitment
        "referral": "identityaddress", (base58) address of the referring identity if there is one
        "parent"  : "namestr",     (string) name of the parent if not Verus or Verus test
        "nameid"  : "address",     (base58) identity address for this identity if it is created
    }
}

Examples:
> verus registernamecommitment "name"
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "registernamecommitment", "params": ["name"] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/



EXAMPLES & OUTPUTS/RESULTS:

1. for the root ID pear.vrsctest@:

./verus registernamecommitment "Pear" "RGi75h173LD84tTThCu73B9Dp6rupM5zoz" "dev7@" "vrsctest" "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"

{
  "txid": "58a848ccf0a7ba9cc2fa530e693fbe846de545650257d3890ed2a00992472806",
  "namereservation": {
    "version": 1,
    "name": "Pear",
    "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
    "salt": "cbb3c336f65598d8c8bb471ba264e8b0baafc4878e83cd1600424e39e505148c",
    "referral": "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX",
    "nameid": "i96dJjh7F8qs8LRMFWoPCiR8dWoNrtCLnz"
  }
}



2. for the sub-ID pear.kaiju@:

./verus registernamecommitment "Pear" "RGi75h173LD84tTThCu73B9Dp6rupM5zoz" "crypto.kaiju@" "kaiju" "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"


{
  "txid": "ae1b27aec77140b90e58d5632b619e310c0a944ec548a1189d722d721c5c41ca",
  "namereservation": {
    "version": 1,
    "name": "Pear",
    "parent": "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f",
    "salt": "4faa8261190bfe6b99beae206a8d2a599084ac013242712e1c3f1272e13dff05",
    "referral": "iJqxRXsVCUAm7XScGR46AV2fPTVDohUD7T",
    "nameid": "iRJPTKsqhSTvBwsYPV8uD2bptLwkUbV6Kw"
  }
}



