GETINFO and GETMININGINFO help commands & examples/outputs:

notes:
- getinfo and getmininginfo can be used to populate or check certain data
- for example it can fetch the current block height, among other data


GETINFO

./verus help getinfo

getinfo

Returns an object containing various state info.

Result:
{
  "version": xxxxx,           (numeric) the server version
  "protocolversion": xxxxx,   (numeric) the protocol version
  "walletversion": xxxxx,     (numeric) the wallet version
  "blocks": xxxxxx,           (numeric) the current number of blocks processed in the server
  "timeoffset": xxxxx,        (numeric) the time offset
  "connections": xxxxx,       (numeric) the number of connections
  "tls_established": xxxxx,   (numeric) the number of TLS connections established
  "tls_verified": xxxxx,      (numeric) the number of TLS connection with validated certificates
  "proxy": "host:port",     (string, optional) the proxy used by the server
  "difficulty": xxxxxx,       (numeric) the current difficulty
  "testnet": true|false,      (boolean) if the server is using testnet or not
  "keypoololdest": xxxxxx,    (numeric) the timestamp (seconds since GMT epoch) of the oldest pre-generated key in the key pool
  "keypoolsize": xxxx,        (numeric) how many new keys are pre-generated
  "unlocked_until": ttt,      (numeric) the timestamp in seconds since epoch (midnight Jan 1 1970 GMT) that the wallet is unlocked for transfers, or 0 if the wallet is locked
  "paytxfee": x.xxxx,         (numeric) the transaction fee set in VRSC/kB
  "relayfee": x.xxxx,         (numeric) minimum relay fee for non-free transactions in VRSC/kB
  "errors": "..."           (string) any error messages
}

Examples:
> verus getinfo 
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getinfo", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/


getinfo EXAMPLE & RESULT/OUTPUT:

./verus getinfo

{
  "VRSCversion": "1.2.9-5",
  "version": 2000753,
  "protocolversion": 170010,
  "chainid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "notarychainid": "iCtawpxUiCc2sEupt7Z4u8SDAncGZpgSKm",
  "name": "VRSCTEST",
  "notarizedroot": {
    "version": 1,
    "type": 1,
    "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
    "height": 550004,
    "stateroot": "e94ea7fb6559db0de4af08ce4cb613b50a295737485f31d24b746dcd6d1b6f0d",
    "blockhash": "38bd3bae57286ab6e2b24e25cf5cc2f5a909fedc89739d73929e27744c18080d",
    "power": "000000000000004ae46664599fad225d0000000000000000000436fecd9bcc9f"
  },
  "walletversion": 60000,
  "blocks": 560900,
  "longestchain": 560900,
  "timeoffset": -4,
  "tiptime": 1747785780,
  "nextblocktime": 1747785823,
  "connections": 5,
  "proxy": "",
  "difficulty": 110623496.4510633,
  "testnet": true,
  "keypoololdest": 1725431550,
  "keypoolsize": 101,
  "paytxfee": 0.0001,
  "tls_established": 5,
  "tls_verified": 0,
  "relayfee": 0.000001,
  "errors": "",
  "CCid": 1,
  "p2pport": 18842,
  "rpcport": 18843,
  "magic": -596868954,
  "premine": 5000000000000000,
  "reward": "600000000",
  "halving": "1051924",
  "decay": "0",
  "endsubsidy": "0",
  "veruspos": 50
}



GETMININGINFO


./verus help getmininginfo

getmininginfo

Returns a json object containing mining-related information.
Result:
{
  "blocks": nnn,             (numeric) The current block
  "currentblocksize": nnn,   (numeric) The last block size
  "currentblocktx": nnn,     (numeric) The last block transaction
  "averageblockfees": xxx.xxxxx (numeric) The average block fees, in addition to block reward, over the past 100 blocks
  "difficulty": xxx.xxxxx    (numeric) The current difficulty
  "stakingsupply": xxx.xxxxx (numeric) The current estimated total staking supply
  "errors": "..."          (string) Current errors
  "generate": true|false     (boolean) If the generation is on or off (see getgenerate or setgenerate calls)
  "genproclimit": n          (numeric) The processor limit for generation. -1 if no generation. (see getgenerate or setgenerate calls)
  "localsolps": xxx.xxxxx    (numeric) The average local solution rate in Sol/s since this node was started
  "networksolps": x          (numeric) The estimated network solution rate in Sol/s
  "pooledtx": n              (numeric) The size of the mem pool
  "testnet": true|false      (boolean) If using testnet or not
  "chain": "xxxx",         (string) current network name as defined in BIP70 (main, test, regtest)
  "generate": true|false     (boolean) If this instance is mining or staking
  "staking": true|false      (boolean) If staking
  "numthreads": n            (numeric) Number of CPU threads mining
  "mergemining": n           (numeric) Number of blockchains we are merge mining with
  "mergeminedchains": []     (optional, list of names) Blockchain names that are being merge mined with this blockchain
}

Examples:
> verus getmininginfo 
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getmininginfo", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/



getmininginfo EXAMPLE & RESULT/OUTPUT:

./verus getmininginfo

{
  "blocks": 560901,
  "currentblocksize": 0,
  "currentblocktx": 0,
  "averageblockfees": 0.000008,
  "difficulty": 115056707.7419983,
  "stakingsupply": 31396662.34625959,
  "errors": "",
  "genproclimit": 0,
  "localhashps": 0,
  "networkhashps": 27380177,
  "pooledtx": 0,
  "testnet": true,
  "chain": "main",
  "generate": false,
  "staking": false,
  "numthreads": 0,
  "mergemining": 0
}


