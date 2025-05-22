registeridentity help command followed by examples with outputs:

notes:
- registernamecommitment and registeridentity are used in the workflow to create a VerusID
- the resulting txid from "registernamecommitment" is used as part of the "registeridentity" command
- IDs have required parameters and optional parameters. Required parameters include "name", "primaryaddresses", and "minimumsignatures". Optional parameters include "privateaddress", "revocationauthority", "recoveryauthority", "timelock", "contentmultimap", and more.
- revocationauthority and recoveryauthority can be the same ID, or they can be 2 different ID's.
- the command's output/result is a txid



./verus help registeridentity

registeridentity "jsonidregistration" (returntx) feeoffer sourceoffunds



Arguments
{
    "txid" : "hexid",          (hex)    the transaction ID of the name commitment for this ID name
    "namereservation" :
    {
        "name": "namestr",     (string) the unique name in this commitment
        "salt": "hexstr",      (hex)    salt used to hide the commitment
        "referral": "identityID", (name@ or address) must be a valid ID to use as a referrer to receive a discount
    },
    "identity" :
    {
        "name": "namestr",     (string) the unique name for this identity
        ...
    }
}
returntx                           (bool, optional) default=false if true, return a transaction for additional signatures rather than committing it
feeoffer                           (amount, optional) amount to offer miner/staker for the registration fee, if missing, uses standard price
sourceoffunds                      (addressorid, optional) optional address to use for source of funds. if not specified, transparent wildcard "*" is used


Result:
   transactionid                   (hexstr)

Examples:
> verus registeridentity jsonidregistration
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "registeridentity", "params": [jsonidregistration] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/



EXAMPLES & OUTPUTS/RESULTS:


1. for the root ID pear.vrsctest@:

./verus registeridentity '{"txid": "58a848ccf0a7ba9cc2fa530e693fbe846de545650257d3890ed2a00992472806",
  "namereservation": {
    "version": 1,
    "name": "Pear",
    "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
    "salt": "cbb3c336f65598d8c8bb471ba264e8b0baafc4878e83cd1600424e39e505148c",
    "referral": "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX",
    "nameid": "i96dJjh7F8qs8LRMFWoPCiR8dWoNrtCLnz"}, "identity":{"name":"Pear", "primaryaddresses":["RGi75h173LD84tTThCu73B9Dp6rupM5zoz"], "minimumsignatures":1}}' "" "80" "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"

2cb7609371693056aa05e1d0f5ff116a6d4f95889ef1c5154d2298e7c7ebd961


    2. for the sub-ID pear.kaiju@:


./verus registeridentity '{"txid": "ae1b27aec77140b90e58d5632b619e310c0a944ec548a1189d722d721c5c41ca",
  "namereservation": {
    "version": 1,
    "name": "Pear",
    "parent": "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f",
    "salt": "4faa8261190bfe6b99beae206a8d2a599084ac013242712e1c3f1272e13dff05",
    "referral": "iJqxRXsVCUAm7XScGR46AV2fPTVDohUD7T",
    "nameid": "iRJPTKsqhSTvBwsYPV8uD2bptLwkUbV6Kw"}, "identity":{"name":"Pear.kaiju", "primaryaddresses":["RGi75h173LD84tTThCu73B9Dp6rupM5zoz"], "minimumsignatures":1}}' "" "59.28850630" "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"

d70f41e29b4c82267bef0b42bfa1dafd6550b7301cccacafea64c102f0f0bd7e




    3. registeridentity including privateaddress, revocationauthority, and recoveryauthority:


./verus registeridentity '{"txid": "f04f38ea5c173f82cab8b4bbe0574ea0612c87006787950c41f9cbbe9a7b551a",
  "namereservation": {
    "version": 1,
    "name": "AI2",
    "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
    "salt": "3e88aedcfe8cb81270302b44e8b80bfb80be784bac05a6a3bc7dff358ef470cf",
    "referral": "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX",
    "nameid": "iQjrxAJrdWbmkAhVfWMA9zEXPen5BrU9AN"}, "identity":{"name":"AI2", "primaryaddresses":["RGi75h173LD84tTThCu73B9Dp6rupM5zoz"], "minimumsignatures":1, "privateaddress":"zs1acdxwfmcaqk72s0ktjwvj3sp7wrlwyg6qy7elcjq6c4xt937w9z8gvfeq6zqj3p3spdwy4ndt3g", "revocationauthority":"dev7@", "recoveryauthority":"dev28@"}}' "" "80" "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"

667f6cb804a31063532882b5a524aa02cd5f0b434ee9c9d194a131fd77b38d3a
