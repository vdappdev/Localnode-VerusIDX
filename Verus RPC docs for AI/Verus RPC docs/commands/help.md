Not all of these commands are current or useful.  Some are no longer used.  For example I don't think "jumblr" does anything anymore.

Here is the help command output for Verus & PBaaS chains:


help

== Addressindex ==
getaddressbalance
getaddressdeltas
getaddressmempool
getaddresstxids
getaddressutxos
getsnapshot

== Blockchain ==
clearrawmempool
coinsupply <height>
getbestblockhash
getblock "hash|height" ( verbosity )
getblockchaininfo
getblockcount
getblockdeltas "blockhash"
getblockhash index
getblockhashes timestamp
getblockheader "hash" ( verbose )
getchaintips
getchaintxstats
getdifficulty
getmempoolinfo
getrawmempool ( verbose )
getspentinfo
gettxout "txid" n ( includemempool )
gettxoutproof ["txid",...] ( blockhash )
gettxoutsetinfo
kvsearch key
kvupdate key "value" days passphrase
minerids needs height
notaries height timestamp
processupgradedata {upgradedata}
verifychain ( checklevel numblocks )
verifytxoutproof "proof"
z_gettreestate "hash|height"

== Control ==
getinfo
help ( "command" )
stop

== Crosschain ==
MoMoMdata symbol kmdheight ccid
assetchainproof needs a txid
calc_MoM height MoMdepth
getNotarisationsForBlock blockHash
height_MoM height
migrate_completeimporttransaction importTx
migrate_converttoexport rawTx dest_symbol export_amount
migrate_createimporttransaction burnTx payouts
scanNotarisationsDB blockHeight symbol [blocksLimit=1440]

== Disclosure ==
z_getpaymentdisclosure "txid" "js_index" "output_index" ("message") 
z_validatepaymentdisclosure "paymentdisclosure"

== Generating ==
generate numblocks
getgenerate
setgenerate generate ( genproclimit )

== Identity ==
getidentitieswithaddress '{"address":"validprimaryaddress","fromheight":height, "toheight":height, "unspent":false}'
getidentitieswithrecovery '{"identityid":"idori-address", "fromheight":height, "toheight":height, "unspent":false}'
getidentitieswithrevocation '{"identityid":"idori-address", "fromheight":height, "toheight":height, "unspent":false}'
getidentity "name@ || iid" (height) (txproof) (txproofheight)
getidentitycontent "name@ || iid" (heightstart) (heightend) (txproofs) (txproofheight) (vdxfkey) (keepdeleted)
getidentityhistory "name@ || iid" (heightstart) (heightend) (txproofs) (txproofheight)
getidentitytrust '["id",...]'
listidentities (includecanspend) (includecansign) (includewatchonly)
recoveridentity "jsonidentity" (returntx) (tokenrecover) (feeoffer) (sourceoffunds)
registeridentity "jsonidregistration" (returntx) feeoffer sourceoffunds
registernamecommitment "name" "controladdress" ("referralidentity") ("parentnameorid") ("sourceoffunds")
revokeidentity "nameorID" (returntx) (tokenrevoke) (feeoffer) (sourceoffunds)
setidentitytimelock "id@" '{"unlockatblock":absoluteblockheight || "setunlockdelay":numberofblocksdelayafterunlock}' (returntx) (feeoffer) (sourceoffunds)
setidentitytrust '{"clearall": bool, "setratings":{"id":JSONRatingObject,...}, "removeratings":["id",...], "identitytrustmode":<n>}'
signdata '{"address":"i-address or friendly name to sign with (t-address will result in simple signature w/indicated hash and prefix, nothing else)",
signfile "address or identity" "filepath/filename" "currentsig"
signmessage "address or identity" "message" "currentsig"
updateidentity "jsonidentity" (returntx) (tokenupdate) (feeoffer) (sourceoffunds)
verifyfile "address or identity" "signature" "filepath/filename" "checklatest"
verifyhash "address or identity" "signature" "hexhash" "checklatest"
verifymessage "address or identity" "signature" "message" "checklatest"
verifysignature '{"address":"i-address or friendly name (t-address checks on simple signature w/hash and prefix, nothing else)",

== Marketplace ==
closeoffers ('["offer1_txid", "offer2_txid", ...]') (transparentorprivatefundsdestination) (privatefundsdestination)
getoffers "currencyorid" (iscurrency) (withtx)
listopenoffers (unexpired) (expired)'
makeoffer fromaddress '{"changeaddress":"transparentoriaddress", "expiryheight":blockheight, "offer":{"currency":"anycurrency", "amount":...} | {"identity":"idnameoriaddress",...}', "for":{"address":..., "currency":"anycurrency", "amount":...} | {"name":"identityforswap","parent":"parentid","primaryaddresses":["R-address(s)"],"minimumsignatures":1,...}}' (returntx) (feeamount)
takeoffer fromaddress '{"txid":"txid" | "tx":"hextx", "changeaddress":"transparentoriaddress", "deliver":"fullidnameoriaddresstodeliver" | {"currency":"currencynameorid","amount":n}, "accept":{"address":"addressorid","currency":"currencynameorid","amount":n} | {identitydefinition} | {"txout":{"serializedtxout"}}}' (returntx) (feeamount)

== Mining ==
getblocksubsidy height
getblocktemplate ( "jsonrequestobject" )
getlocalsolps
getminingdistribution
getmininginfo
getnetworkhashps ( blocks height )
getnetworksolps ( blocks height )
prioritisetransaction <txid> <priority delta> <fee delta>
setminingdistribution ( "jsonminingdistribution" )
submitblock "hexdata" ( "jsonparametersobject" )

== Multichain ==
addmergedblock "hexdata" ( "jsonparametersobject" )
definecurrency '{"name": "coinortokenname", ..., "nodes":[{"networkaddress":"identity"},..]}'\
estimateconversion '{"currency":"name","convertto":"name","amount":n} | [array of conversions using one basket]'
getbestproofroot '{"proofroots":["version":n,"type":n,"systemid":"currencyidorname","height":n,                   "stateroot":"hex","blockhash":"hex","power":"hex"],"lastconfirmed":n}'
getcurrency "currencyname"
getcurrencyconverters "currency1" "currency2" ... |
getcurrencystate "currencynameorid" ("n") ("conversiondatacurrency")
getcurrencytrust '["currencyid",...]'
getexports "chainname" (heightstart) (heightend)
getimports "chainname" (startheight) (endheight)
getinitialcurrencystate "name"
getlastimportfrom "systemname"
getlaunchinfo "currencyid"
getnotarizationdata "currencynameorid" (getevidence) (separatecounterevidence)
getnotarizationproofs '[{"type":"vrsc::evidence.skipchallenge" || "iCwxpRL6h3YeCRtGjgQSsqoKdZCuM4Dxaf",
getpendingtransfers "chainname"
getreservedeposits "currencyname" (returnutxos)
getsaplingtree "n"
listcurrencies ({query object}) startblock endblock
refundfailedlaunch "currencyid"
sendcurrency "fromaddress" '[{"address":... ,"amount":...},...]' (minconfs) (feeamount) (returntxtemplate)
setcurrencytrust '{"clearall": bool, "setratings":[{"currencyid":JSONRatingObject},...], "removeratings":["currencyid",...], "currencytrustmode":<n>}'
submitacceptednotarization "{earnednotarization}" "{notaryevidence}"
submitchallenges '[{"type":"vrsc::evidence.skipchallenge" || "iCwxpRL6h3YeCRtGjgQSsqoKdZCuM4Dxaf" ||
submitimports '{"sourcesystemid":"systemid", "notarizationtxid":"txid", "notarizationtxoutnum":n,
submitmergedblock "hexdata" ( "jsonparametersobject" )

== Network ==
addnode "node" "add|remove|onetry"
clearbanned
disconnectnode "node" 
getaddednodeinfo dns ( "node" )
getconnectioncount
getdeprecationinfo
getnettotals
getnetworkinfo
getpeerinfo
listbanned
ping
setban "ip(/netmask)" "add|remove" (bantime) (absolute)

== Rawtransactions ==
createrawtransaction [{"txid":"id","vout":n},...] {"address":amount,...} ( locktime ) ( expiryheight )
decoderawtransaction "hexstring"
decodescript "hex"
fundrawtransaction "hexstring" '[{"txid":"8892b6c090b51a4eed7a61b72e9c8dbf5ed5bcd5aca6c6819b630acf2cb3fc87","voutnum":1},...]' (changeaddress) (explicitfee)
getrawtransaction "txid" ( verbose )
sendrawtransaction "hexstring" ( allowhighfees )
signrawtransaction "hexstring" ( [{"txid":"id","vout":n,"scriptPubKey":"hex","redeemScript":"hex"},...] ["privatekey1",...] sighashtype )

== Util ==
createmultisig nrequired ["key",...]
estimatefee nblocks
estimatepriority nblocks
invalidateblock "hash"
jumblr_deposit "depositaddress"
jumblr_pause
jumblr_resume
jumblr_secret "secretaddress"
reconsiderblock "hash"
validateaddress "address"
z_validateaddress "zaddr"

== Vdxf ==
getvdxfid "vdxfuri" '{"vdxfkey":"i-address or vdxfkey", "uint256":"hexstr", "indexnum":0}'

== Wallet ==
addmultisigaddress nrequired ["key",...] ( "account" )
backupwallet "destination"
convertpassphrase "walletpassphrase"
decryptdata '{
dumpprivkey "t-addr"
dumpwallet "filename" (omitemptytaddresses)
encryptwallet "passphrase"
getaccount "VRSCTEST_address"
getaccountaddress "account"
getaddressesbyaccount "account"
getbalance ( "account" minconf includeWatchonly )
getcurrencybalance "address" ( minconf ) ( friendlynames ) ( includeshared )
getnewaddress ( "account" )
getrawchangeaddress
getreceivedbyaccount "account" ( minconf )
getreceivedbyaddress "VRSCTEST_address" ( minconf )
gettransaction "txid" ( includeWatchonly )
getunconfirmedbalance
getwalletinfo
importaddress "address" ( "label" rescan )
importprivkey "verusprivkey" ( "label" rescan )
importwallet "filename"
keypoolrefill ( newsize )
listaccounts ( minconf includeWatchonly)
listaddressgroupings
listlockunspent
listreceivedbyaccount ( minconf includeempty includeWatchonly)
listreceivedbyaddress ( minconf includeempty includeWatchonly)
listsinceblock ( "blockhash" target-confirmations includeWatchonly)
listtransactions ( ("account" | '{queryobject}' count from includeWatchonly)
listunspent ( minconf maxconf  ["address",...] includeshared )
lockunspent unlock [{"txid":"txid","vout":n},...]
move "fromaccount" "toaccount" amount ( minconf "comment" )
prunespentwallettransactions "txid"
rescanfromheight (height)
resendwallettransactions
sendfrom "fromaccount" "toVRSCTESTaddress" amount ( minconf "comment" "comment-to" )
sendmany "fromaccount" {"address":amount,...} ( minconf "comment" ["address",...] )
sendtoaddress "VRSCTEST_address" amount ( "comment" "comment-to" subtractfeefromamount )
setaccount "VRSCTEST_address" "account"
settxfee amount
z_exportkey "zaddr" (outputashex)
z_exportviewingkey "zaddr"
z_exportwallet "filename" (omitemptytaddresses)
z_getbalance "address" ( minconf )
z_generateencryptionkey '{("address":"zaddress present in wallet" | "seed":"wallet seed for address", "hdindex":n - address to derive from seed | "rootkey":"extended private key"),
z_getmigrationstatus
z_getnewaddress ( type )
z_getoperationresult (["operationid", ... ]) 
z_getoperationstatus (["operationid", ... ]) 
z_gettotalbalance ( minconf includeWatchonly )
z_importkey "zkey" ( rescan startHeight )
z_importviewingkey "vkey" ( rescan startHeight )
z_importwallet "filename"
z_listaddresses ( includeWatchonly )
z_listoperationids
z_listreceivedbyaddress "address" ( minconf )
z_listunspent ( minconf maxconf includeWatchonly ["zaddr",...] )
z_mergetoaddress ["fromaddress", ... ] "toaddress" ( fee ) ( transparent_limit ) ( shielded_limit ) ( memo )
z_sendmany "fromaddress" [{"address":... ,"amount":...},...] ( minconf ) ( fee )
z_setmigration enabled
z_shieldcoinbase "fromaddress" "tozaddress" ( fee ) ( limit )
z_viewtransaction "txid"
zcbenchmark benchmarktype samplecount
zcrawjoinsplit rawtx inputs outputs vpub_old vpub_new
zcrawkeygen
zcrawreceive zcsecretkey encryptednote
zcsamplejoinsplit