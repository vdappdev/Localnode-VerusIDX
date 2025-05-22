getcurrency help command followed by examples with outputs:

notes:  
- getcurrency "i-address" can be used for retrieving the friendly name of an i-address, for example when getoffers "currency name" is used it returns info that displays i-addresses instead of friendly names. (getidentity "i-address" would also work for retrieving the currency's friendly name too since the currency name is based on the id@ name)


./verus help getcurrency
getcurrency "currencyname"

Returns a complete definition for any given chain if it is registered on the blockchain. If the chain requested

is NULL, chain definition of the current chain is returned.

Arguments
1. "currencyname"            (string, optional) name of the chain to look for. no parameter returns current chain in daemon.

Result:
  {
    "version" : n,                           (int) version of this chain definition
    "name" : "string",                     (string) name or symbol of the chain, same as passed
    "fullyqualifiedname" : "string",       (string) name or symbol of the chain with all parent namespaces, separated by "."
    "currencyid" : "i-address",            (string) string that represents the currency ID, same as the ID behind the currency
    "currencyidhex" : "hex",               (string) hex representation of currency ID, getcurrency API supports "hex:currencyidhex"
    "parent" : "i-address",                (string) parent blockchain ID
    "systemid" : "i-address",              (string) system on which this currency is considered to run
    "launchsystemid" : "i-address",        (string) system from which this currency was launched
    "notarizationprotocol" : n               (int) protocol number that determines variations in cross-chain or bridged notarizations
    "proofprotocol" : n                      (int) protocol number that determines variations in cross-chain or bridged proofs
    "startblock" : n,                        (int) block # on this chain, which must be notarized into block one of the chain
    "endblock" : n,                          (int) block # after which, this chain's useful life is considered to be over
    "currencies" : "["i-address", ...]", (stringarray) currencies that can be converted to this currency at launch or makeup a liquidity basket
    "weights" : "[n, ...]",                (numberarray) relative currency weights (only returned for a liquidity basket)
    "conversions" : "[n, ...]",            (numberarray) pre-launch conversion rates for non-fractional currencies
    "minpreconversion" : "[n, ...]",       (numberarray) minimum amounts required in pre-conversions for currency to launch
    "currencies" : "["i-address", ...]", (stringarray) currencies that can be converted to this currency at launch or makeup a liquidity basket
    "currencynames" : "{"i-address":"fullname",...}", (obj) i-addresses mapped to fully qualified names of all sub-currencies
    "initialsupply" : n,                     (number) initial currency supply for fractional currencies before preallocation or issuance
    "prelaunchcarveout" : n,                 (number) pre-launch percentage of proceeds for fractional currency sent to launching ID
    "preallocations" : "[{"i-address":n}, ...]", (objarray) VerusIDs and amounts for pre-allocation at launch
    "initialcontributions" : "[n, ...]",   (numberarray) amounts of pre-conversions reserved for launching ID
    "idregistrationfees" : n,                (number) base cost of IDs for this currency namespace in this currency
    "idreferrallevels" : n,                  (int) levels of ID referrals (only for native PBaaS chains and IDs)
    "idimportfees" : n,                      (number) fees required to import an ID to this system (only for native PBaaS chains and IDs)
    "eras" : "[obj, ...]",                 (objarray) different chain phases of rewards and convertibility
    {
      "reward" : "[n, ...]",               (int) reward start for each era in native coin
      "decay" : "[n, ...]",                (int) exponential or linear decay of rewards during each era
      "halving" : "[n, ...]",              (int) blocks between halvings during each era
      "eraend" : "[n, ...]",               (int) block marking the end of each era
      "eraoptions" : "[n, ...]",           (int) options (reserved)
    }
    "nodes"      : "[obj, ..]",    (objectarray, optional) up to 8 nodes that can be used to connect to the blockchain      [{
         "nodeidentity" : "txid", (string,  optional) internet, TOR, or other supported address for node
         "paymentaddress" : n,     (int,     optional) rewards payment address
       }, .. ]
    "lastconfirmedcurrencystate" : {
     }
    "besttxid" : "txid"
     }
    "confirmednotarization" : {
     }
    "confirmedtxid" : "txid"
  }

Examples:
> verus getcurrency "currencyname"
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getcurrency", "params": ["currencyname"] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/



EXAMPLES & OUTPUTS/RESULTS:


./verus getcurrency gamesession5
{
  "version": 1,
  "options": 33,
  "name": "gamesession5",
  "currencyid": "i814vg9MCgn26oypfcvRKMdQPVCmS6P8G7",
  "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "notarizationprotocol": 1,
  "proofprotocol": 1,
  "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "startblock": 191206,
  "endblock": 0,
  "currencies": [
    "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq"
  ],
  "weights": [
    1
  ],
  "conversions": [
    0
  ],
  "initialsupply": 1,
  "prelaunchcarveout": 0,
  "initialcontributions": [
    0
  ],
  "idregistrationfees": 0.000001,
  "idreferrallevels": 3,
  "idimportfees": 0,
  "currencyidhex": "ffe9e8b17fa7587d385afdfd03cc94586645a731",
  "fullyqualifiedname": "gamesession5",
  "magicnumber": -1873430010,
  "currencynames": {
    "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": "VRSCTEST"
  },
  "definitiontxid": "82bdf464d24a27a0e733902e3c1e67c703a36f0d99fb09609160d3d1adac4cc6",
  "definitiontxout": 1,
  "bestheight": 344968,
  "lastconfirmedheight": 344968,
  "bestcurrencystate": {
    "flags": 49,
    "version": 1,
    "currencyid": "i814vg9MCgn26oypfcvRKMdQPVCmS6P8G7",
    "reservecurrencies": [
      {
        "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "weight": 1,
        "reserves": 102.99172451,
        "priceinreserve": 1.00021534
      }
    ],
    "initialsupply": 1,
    "emitted": 0,
    "supply": 102.96955101,
    "currencies": {
      "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
        "reservein": 0,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 1.00040024,
        "viaconversionprice": 1.00040024,
        "fees": 0.0002,
        "conversionfees": 0,
        "priorweights": 1
      }
    },
    "primarycurrencyfees": 0,
    "primarycurrencyconversionfees": 0,
    "primarycurrencyout": -9.9e-7,
    "preconvertedout": 0
  },
  "lastconfirmedcurrencystate": {
    "flags": 49,
    "version": 1,
    "currencyid": "i814vg9MCgn26oypfcvRKMdQPVCmS6P8G7",
    "reservecurrencies": [
      {
        "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "weight": 1,
        "reserves": 102.99172451,
        "priceinreserve": 1.00021534
      }
    ],
    "initialsupply": 1,
    "emitted": 0,
    "supply": 102.96955101,
    "currencies": {
      "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
        "reservein": 0,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 1.00040024,
        "viaconversionprice": 1.00040024,
        "fees": 0.0002,
        "conversionfees": 0,
        "priorweights": 1
      }
    },
    "primarycurrencyfees": 0,
    "primarycurrencyconversionfees": 0,
    "primarycurrencyout": -9.9e-7,
    "preconvertedout": 0
  }
}



./verus getcurrency usd
{
  "version": 1,
  "options": 40,
  "name": "USD",
  "currencyid": "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
  "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "notarizationprotocol": 1,
  "proofprotocol": 2,
  "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "startblock": 150,
  "endblock": 0,
  "currencies": [
    "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq"
  ],
  "conversions": [
    1
  ],
  "preallocations": [
    {
      "i6kcKLQrCAvmajP8LrVxEdPeZajkSjXLvW": 100000000
    }
  ],
  "initialcontributions": [
    0
  ],
  "idregistrationfees": 100,
  "idreferrallevels": 3,
  "idimportfees": 0.02,
  "currencyidhex": "3c0d149e82c38d062eaa4bd87dc8c155e381d884",
  "fullyqualifiedname": "USD",
  "magicnumber": 1819195614,
  "currencynames": {
    "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": "VRSCTEST"
  },
  "definitiontxid": "9ea9775f997ff9e24121cec81b3fb9c014c98bfdeb0361e4fd5d9e78fb99e01f",
  "definitiontxout": 1,
  "bestheight": 344968,
  "lastconfirmedheight": 344968,
  "bestcurrencystate": {
    "flags": 48,
    "version": 1,
    "currencyid": "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
    "launchcurrencies": [
      {
        "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "weight": 0,
        "reserves": 1,
        "priceinreserve": 1
      }
    ],
    "initialsupply": 0,
    "emitted": 0,
    "supply": 100000000,
    "currencies": {
      "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
        "reservein": 0,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 1,
        "viaconversionprice": 0,
        "fees": 0,
        "conversionfees": 0,
        "priorweights": 0
      }
    },
    "primarycurrencyfees": 0,
    "primarycurrencyconversionfees": 0,
    "primarycurrencyout": 0,
    "preconvertedout": 0
  },
  "lastconfirmedcurrencystate": {
    "flags": 48,
    "version": 1,
    "currencyid": "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
    "launchcurrencies": [
      {
        "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "weight": 0,
        "reserves": 1,
        "priceinreserve": 1
      }
    ],
    "initialsupply": 0,
    "emitted": 0,
    "supply": 100000000,
    "currencies": {
      "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
        "reservein": 0,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 1,
        "viaconversionprice": 0,
        "fees": 0,
        "conversionfees": 0,
        "priorweights": 0
      }
    },
    "primarycurrencyfees": 0,
    "primarycurrencyconversionfees": 0,
    "primarycurrencyout": 0,
    "preconvertedout": 0
  }
}


 ./verus getcurrency kaiju
{
  "version": 1,
  "options": 41,
  "name": "Kaiju",
  "currencyid": "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f",
  "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "notarizationprotocol": 1,
  "proofprotocol": 1,
  "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "startblock": 14285,
  "endblock": 0,
  "currencies": [
    "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
    "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
    "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3",
    "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV"
  ],
  "weights": [
    0.25,
    0.25,
    0.25,
    0.25
  ],
  "conversions": [
    0,
    0,
    0,
    0
  ],
  "initialsupply": 100000,
  "prelaunchcarveout": 0,
  "initialcontributions": [
    0,
    0,
    0,
    0
  ],
  "idregistrationfees": 15,
  "idreferrallevels": 2,
  "idimportfees": 1e-8,
  "currencyidhex": "725ccb001e72746ac2c99243fb7ba5a593b46e96",
  "fullyqualifiedname": "Kaiju",
  "magicnumber": -1703450999,
  "currencynames": {
    "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": "VRSCTEST",
    "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": "USD",
    "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3": "BTC",
    "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV": "KMD"
  },
  "definitiontxid": "30e8b68e58cf425aa77176e27812fb0333d8655d81f12ac157831628c79ee859",
  "definitiontxout": 1,
  "bestheight": 344968,
  "lastconfirmedheight": 344968,
  "bestcurrencystate": {
    "flags": 49,
    "version": 1,
    "currencyid": "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f",
    "reservecurrencies": [
      {
        "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "weight": 0.25,
        "reserves": 521.16547781,
        "priceinreserve": 0.0233897
      },
      {
        "currencyid": "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
        "weight": 0.25,
        "reserves": 4232.02908016,
        "priceinreserve": 0.18993184
      },
      {
        "currencyid": "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3",
        "weight": 0.25,
        "reserves": 0.06048833,
        "priceinreserve": 0.00000271
      },
      {
        "currencyid": "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV",
        "weight": 0.25,
        "reserves": 8140.68889477,
        "priceinreserve": 0.36535099
      }
    ],
    "initialsupply": 100000,
    "emitted": 0,
    "supply": 89127.32105258,
    "currencies": {
      "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
        "reservein": 4.999375,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 0.02330537,
        "viaconversionprice": 0.02330537,
        "fees": 0.0014501,
        "conversionfees": 0.00125,
        "priorweights": 0.25
      },
      "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": {
        "reservein": 0,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 0.19039002,
        "viaconversionprice": 0.19039002,
        "fees": 0,
        "conversionfees": 0,
        "priorweights": 0.25
      },
      "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3": {
        "reservein": 0,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 0.00000272,
        "viaconversionprice": 0.00000272,
        "fees": 0,
        "conversionfees": 0,
        "priorweights": 0.25
      },
      "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV": {
        "reservein": 0,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 0.36623235,
        "viaconversionprice": 0.36623235,
        "fees": 0,
        "conversionfees": 0,
        "priorweights": 0.25
      }
    },
    "primarycurrencyfees": 0,
    "primarycurrencyconversionfees": 0,
    "primarycurrencyout": 214.48919283,
    "preconvertedout": 0
  },
  "lastconfirmedcurrencystate": {
    "flags": 49,
    "version": 1,
    "currencyid": "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f",
    "reservecurrencies": [
      {
        "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "weight": 0.25,
        "reserves": 521.16547781,
        "priceinreserve": 0.0233897
      },
      {
        "currencyid": "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
        "weight": 0.25,
        "reserves": 4232.02908016,
        "priceinreserve": 0.18993184
      },
      {
        "currencyid": "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3",
        "weight": 0.25,
        "reserves": 0.06048833,
        "priceinreserve": 0.00000271
      },
      {
        "currencyid": "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV",
        "weight": 0.25,
        "reserves": 8140.68889477,
        "priceinreserve": 0.36535099
      }
    ],
    "initialsupply": 100000,
    "emitted": 0,
    "supply": 89127.32105258,
    "currencies": {
      "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
        "reservein": 4.999375,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 0.02330537,
        "viaconversionprice": 0.02330537,
        "fees": 0.0014501,
        "conversionfees": 0.00125,
        "priorweights": 0.25
      },
      "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": {
        "reservein": 0,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 0.19039002,
        "viaconversionprice": 0.19039002,
        "fees": 0,
        "conversionfees": 0,
        "priorweights": 0.25
      },
      "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3": {
        "reservein": 0,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 0.00000272,
        "viaconversionprice": 0.00000272,
        "fees": 0,
        "conversionfees": 0,
        "priorweights": 0.25
      },
      "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV": {
        "reservein": 0,
        "primarycurrencyin": 0,
        "reserveout": 0,
        "lastconversionprice": 0.36623235,
        "viaconversionprice": 0.36623235,
        "fees": 0,
        "conversionfees": 0,
        "priorweights": 0.25
      }
    },
    "primarycurrencyfees": 0,
    "primarycurrencyconversionfees": 0,
    "primarycurrencyout": 214.48919283,
    "preconvertedout": 0
  }
}


