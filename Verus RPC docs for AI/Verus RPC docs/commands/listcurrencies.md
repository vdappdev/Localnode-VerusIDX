listcurrencies help command followed by examples with outputs:


./verus help listcurrencies

listcurrencies ({query object}) startblock endblock

Returns a complete definition for any given chain if it is registered on the blockchain. If the chain requested

is NULL, chain definition of the current chain is returned.

Arguments
{                                    (json, optional) specify valid query conditions
   "launchstate" :                   ("prelaunch" | "launched" | "refund" | "complete") (optional) return only currencies in that state
   "systemtype" :                    ("local" | "imported" | "gateway" | "pbaas")
   "fromsystem" :                    ("systemnameeorid") default is the local chain, but if currency is from another system, specify here
   "converter": ["currency1", ("currency2")] (array, optional) default empty, only return fractional currency converters of one or more currencies
}

Result:
[
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
  }, ...
]

Examples:
> verus listcurrencies true
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "listcurrencies", "params": [true] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/



EXAMPLE & RESULT/OUTPUT:


[
  {
    "currencydefinition": {
      "version": 1,
      "options": 33,
      "name": "kneipe-veth-vrsctest-usdt-basket",
      "currencyid": "iRqPwMWVawLy5uNsv6UPUjtEhmnX63rtGZ",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 218100,
      "endblock": 0,
      "currencies": [
        "iNZzqYdmfCPCcVSTBjbPT8Q7rqeFohxATu",
        "iCtawpxUiCc2sEupt7Z4u8SDAncGZpgSKm",
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2"
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
      "prelaunchdiscount": 0.5,
      "initialsupply": 100,
      "prelaunchcarveout": 0.1,
      "initialcontributions": [
        0,
        0,
        0,
        0
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "c6ce952f8d4f8ea0cd89d607a67f2ba1e93e45f5",
      "fullyqualifiedname": "kneipe-veth-vrsctest-usdt-basket",
      "definitiontxid": "d878b9185fa8e914b5f1d4fdc088e83448de2ca912b173990e034fc34d709203",
      "definitiontxout": 1
    },
    "bestheight": 218370,
    "besttxid": "23a7354fdefa6687c19d66b7a04f0de528d60213166cfb1f78a82b3eb1b7b9fe",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 49,
      "version": 1,
      "currencyid": "iRqPwMWVawLy5uNsv6UPUjtEhmnX63rtGZ",
      "reservecurrencies": [
        {
          "currencyid": "iNZzqYdmfCPCcVSTBjbPT8Q7rqeFohxATu",
          "weight": 0.1125,
          "reserves": 819677.09591445,
          "priceinreserve": 73596.14778131
        },
        {
          "currencyid": "iCtawpxUiCc2sEupt7Z4u8SDAncGZpgSKm",
          "weight": 0.1125,
          "reserves": 0.900025,
          "priceinreserve": 0.08081032
        },
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.1125,
          "reserves": 238.47173681,
          "priceinreserve": 21.41160375
        },
        {
          "currencyid": "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
          "weight": 0.1125,
          "reserves": 450.0125,
          "priceinreserve": 40.40516273
        }
      ],
      "initialsupply": 100,
      "emitted": 0,
      "supply": 99,
      "currencies": {
        "iNZzqYdmfCPCcVSTBjbPT8Q7rqeFohxATu": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 3449.95126691,
          "lastconversionprice": 73905.90771549,
          "viaconversionprice": 73733.48169118,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.1125
        },
        "iCtawpxUiCc2sEupt7Z4u8SDAncGZpgSKm": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.08081032,
          "viaconversionprice": 0.08077215,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.1125
        },
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 0.99975,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 21.36163941,
          "viaconversionprice": 21.40146652,
          "fees": 0.0007001,
          "conversionfees": 0.0005,
          "priorweights": 0.1125
        },
        "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 40.40516273,
          "viaconversionprice": 40.38607543,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.1125
        }
      },
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 33,
      "name": "bankroll",
      "currencyid": "i3zeobcYAJt6rkteDehA3UKnw4HydPunwR",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 475260,
      "endblock": 0,
      "currencies": [
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "iDMAoXEjZLkpofokBGsVwen7YEwo1iujMQ",
        "iPJCmjFfPTPSEecRQ4htkaCmJ3C4YWDZHa",
        "iGhBps9rmbN7U544dZY7nx2rfg26QTh1zY"
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
      "minpreconversion": [
        1e-8,
        1e-8,
        1e-8,
        25000
      ],
      "initialsupply": 1000000,
      "prelaunchcarveout": 0,
      "initialcontributions": [
        0,
        0,
        0,
        0
      ],
      "idregistrationfees": 7.77,
      "idreferrallevels": 3,
      "idimportfees": 3e-8,
      "currencyidhex": "c38567b6bdfa6f16165f30dce35657eac3a1b205",
      "fullyqualifiedname": "bankroll",
      "definitiontxid": "6ed7a21f0b63a4a51e5744fbf55b13233a58992d93c4ff28da4274a1104a9e04",
      "definitiontxout": 1
    },
    "bestheight": 475458,
    "besttxid": "5a2d57b49391fb7a50c61fbc0914bcc942ba12cd6766af7e5250b08065659eba",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 49,
      "version": 1,
      "currencyid": "i3zeobcYAJt6rkteDehA3UKnw4HydPunwR",
      "reservecurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.25,
          "reserves": 0.99950124,
          "priceinreserve": 0.00000399
        },
        {
          "currencyid": "iDMAoXEjZLkpofokBGsVwen7YEwo1iujMQ",
          "weight": 0.25,
          "reserves": 1,
          "priceinreserve": 0.000004
        },
        {
          "currencyid": "iPJCmjFfPTPSEecRQ4htkaCmJ3C4YWDZHa",
          "weight": 0.25,
          "reserves": 1,
          "priceinreserve": 0.000004
        },
        {
          "currencyid": "iGhBps9rmbN7U544dZY7nx2rfg26QTh1zY",
          "weight": 0.25,
          "reserves": 25001,
          "priceinreserve": 0.10001177
        }
      ],
      "initialsupply": 1000000,
      "emitted": 0,
      "supply": 999922.3,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.000004,
          "viaconversionprice": 0.00000398,
          "fees": 0.0002,
          "conversionfees": 0,
          "priorweights": 0.25
        },
        "iDMAoXEjZLkpofokBGsVwen7YEwo1iujMQ": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.000004,
          "viaconversionprice": 0.00000399,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.25
        },
        "iPJCmjFfPTPSEecRQ4htkaCmJ3C4YWDZHa": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.000004,
          "viaconversionprice": 0.00000399,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.25
        },
        "iGhBps9rmbN7U544dZY7nx2rfg26QTh1zY": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.099979,
          "viaconversionprice": 0.09998055,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.25
        }
      },
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": -77.7,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 34,
      "name": "SILQ",
      "currencyid": "iHsm9LsU29kkPVF8hfooFhwfeVb1RD56Gf",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 2,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 546603,
      "endblock": 0,
      "preallocations": [
        {
          "iHsm9LsU29kkPVF8hfooFhwfeVb1RD56Gf": 1000000
        }
      ],
      "idregistrationfees": 0.015,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "ec48c2aa0d3b36dd9ef03b0b1c3f008c1cc6f69d",
      "fullyqualifiedname": "SILQ",
      "definitiontxid": "18ac67027595b094454fc288868dabf9930373ec46ec5adcfab658a594b5cc05",
      "definitiontxout": 1
    },
    "bestheight": 546602,
    "besttxid": "7d0636718341bfd3729236536755c8404c8b7eae190c334825fe30af785f8b98",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iHsm9LsU29kkPVF8hfooFhwfeVb1RD56Gf",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 1000000,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 32,
      "name": "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ_Bach_songs",
      "currencyid": "iNeerwTv6WUFcyjcrvMj6fAYXbQT64z4r3",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 2,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 490400,
      "endblock": 0,
      "preallocations": [
        {
          "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ": 1
        }
      ],
      "idregistrationfees": 0,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "a66c30849455e922f6efe572945ddfe92ac054d2",
      "fullyqualifiedname": "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ_Bach_songs",
      "definitiontxid": "d1f6f336b306bafe848a62ff82e385108cb546233c3268b730437cbceebf1109",
      "definitiontxout": 1
    },
    "bestheight": 490399,
    "besttxid": "31cf219d09b5af564104afdf4616f2318cce46328b76991e014ee431492d3ce1",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iNeerwTv6WUFcyjcrvMj6fAYXbQT64z4r3",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 1,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 40,
      "name": "KMD",
      "currencyid": "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV",
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
      "currencyidhex": "10dc05b8a150a59fdda8e9b1e17c12a725dd283c",
      "fullyqualifiedname": "KMD",
      "definitiontxid": "c1989b5da52e82bf44386e2e759e1d499f476e510bc5d4a2540c265979e0e20b",
      "definitiontxout": 1
    },
    "bestheight": 149,
    "besttxid": "152bcf2b675a782d583cfe891c34b7e9e7a2df16b286460857abbd72e9324cfa",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV",
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
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 32,
      "name": "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ_Bach5_songs",
      "currencyid": "i6Zx7hGLLyDFdf6B6fM5WyWARFeMKG3j4u",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 2,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 490454,
      "endblock": 0,
      "preallocations": [
        {
          "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ": 1
        }
      ],
      "idregistrationfees": 0,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "75b1c98c35d4f8814a8a4de77beaf0edc10fef21",
      "fullyqualifiedname": "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ_Bach5_songs",
      "definitiontxid": "7a37c64b2d8ef60223f34f6e7b41a7d89b3bf59afe4980bf6f468e6762b8af0e",
      "definitiontxout": 1
    },
    "bestheight": 490453,
    "besttxid": "e60f60fda623d8d862d2134836a18c48587b19785b3cccb9c541a2342501cdce",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "i6Zx7hGLLyDFdf6B6fM5WyWARFeMKG3j4u",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 1,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 33,
      "name": "TRIDENTFINAL1",
      "currencyid": "iKQVHvHYV4MRKP3daWwcrDccrrK1JruFvF",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 475115,
      "endblock": 0,
      "currencies": [
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "iDMAoXEjZLkpofokBGsVwen7YEwo1iujMQ",
        "iPJCmjFfPTPSEecRQ4htkaCmJ3C4YWDZHa"
      ],
      "weights": [
        0.25,
        0.5,
        0.25
      ],
      "conversions": [
        0,
        0,
        0
      ],
      "initialsupply": 1000000,
      "prelaunchcarveout": 0,
      "initialcontributions": [
        0,
        0,
        0
      ],
      "idregistrationfees": 1,
      "idreferrallevels": 0,
      "idimportfees": 0.02,
      "currencyidhex": "180d2a926e2958522fc205e9217f2189d08fbeae",
      "fullyqualifiedname": "TRIDENTFINAL1",
      "definitiontxid": "f6ed2667f6e0c0c815133a2334adcdf0349274404c94f3474e9a4fe505dbc212",
      "definitiontxout": 1
    },
    "bestheight": 475114,
    "besttxid": "c2252353bc0d58602279deadc8e28d6ae71db703b3e7f1ecc99593ef5d15bc52",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 37,
      "version": 1,
      "currencyid": "iKQVHvHYV4MRKP3daWwcrDccrrK1JruFvF",
      "reservecurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.25,
          "reserves": 0,
          "priceinreserve": 0.25
        },
        {
          "currencyid": "iDMAoXEjZLkpofokBGsVwen7YEwo1iujMQ",
          "weight": 0.5,
          "reserves": 0,
          "priceinreserve": 0.5
        },
        {
          "currencyid": "iPJCmjFfPTPSEecRQ4htkaCmJ3C4YWDZHa",
          "weight": 0.25,
          "reserves": 0,
          "priceinreserve": 0.25
        }
      ],
      "initialsupply": 1000000,
      "emitted": 0,
      "supply": 0,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.000004,
          "viaconversionprice": 0,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.25
        },
        "iDMAoXEjZLkpofokBGsVwen7YEwo1iujMQ": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.000002,
          "viaconversionprice": 0,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.5
        },
        "iPJCmjFfPTPSEecRQ4htkaCmJ3C4YWDZHa": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.000004,
          "viaconversionprice": 0,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.25
        }
      },
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 33,
      "name": "VRSC-KMD",
      "currencyid": "iL1mYzEzNewFNPFt8APcVn9zGULTQpbWDt",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 201,
      "endblock": 0,
      "currencies": [
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV"
      ],
      "weights": [
        0.5,
        0.5
      ],
      "conversions": [
        0,
        0
      ],
      "initialsupply": 2000000,
      "prelaunchcarveout": 0,
      "initialcontributions": [
        200000,
        1977664.24557094
      ],
      "idregistrationfees": 5,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "12a4852620cf7db58554ed8c20a4e0d484b16ab5",
      "fullyqualifiedname": "VRSC-KMD",
      "definitiontxid": "cc45994867fe63677f5e03e7509ad2099e6913db44821660dfb0770cdd7e1513",
      "definitiontxout": 1
    },
    "bestheight": 471160,
    "besttxid": "6d8e93544e738cd9a7d147fd3050e6a53e0f45442b96f5c364948ac890bb9493",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 49,
      "version": 1,
      "currencyid": "iL1mYzEzNewFNPFt8APcVn9zGULTQpbWDt",
      "reservecurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.5,
          "reserves": 198864.68764732,
          "priceinreserve": 0.19885469
        },
        {
          "currencyid": "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV",
          "weight": 0.5,
          "reserves": 1989659.7361821,
          "priceinreserve": 1.98955973
        }
      ],
      "initialsupply": 2000000,
      "emitted": 0,
      "supply": 2000100.52152042,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 162.92563964,
          "lastconversionprice": 0.19901761,
          "viaconversionprice": 0.1988954,
          "fees": 0.0002001,
          "conversionfees": 0,
          "priorweights": 0.5
        },
        "i8xcvrfKTw8eEiTMjt1dAQxpWcbZeaVMFV": {
          "reservein": 1629.15887534,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 1.98833774,
          "viaconversionprice": 1.98874483,
          "fees": 0.81457942,
          "conversionfees": 0.81457942,
          "priorweights": 0.5
        }
      },
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 32,
      "name": "KAG",
      "currencyid": "i4TLzjJ2JQVVqrWd3JhzxStYkaGbd93Sda",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 546682,
      "endblock": 0,
      "preallocations": [
        {
          "i4TLzjJ2JQVVqrWd3JhzxStYkaGbd93Sda": 1000000
        }
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "69133e3424c78d700aeb8d752f25116958ffbe0a",
      "fullyqualifiedname": "KAG",
      "definitiontxid": "3c36f6b972f89c6e1c28aae552dfde132c4f8da19dd6f215450460a0a94b6716",
      "definitiontxout": 1
    },
    "bestheight": 546681,
    "besttxid": "3569d4f0130f9bb44f43ba6dd4ac96bccceffa67c23c727cdb0eaa78d5e54f4f",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "i4TLzjJ2JQVVqrWd3JhzxStYkaGbd93Sda",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 1000000,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 34,
      "name": "my_collection",
      "currencyid": "iRXE9y35BQfBu4JRTWH6S7fieKTHpJvWyD",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 2,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 217721,
      "endblock": 0,
      "idregistrationfees": 0,
      "idreferrallevels": 0,
      "idimportfees": 0.02,
      "currencyidhex": "1b3c68d7566c8fdae69160f5dea6388ba697d5f1",
      "fullyqualifiedname": "my_collection",
      "definitiontxid": "db3e0db2f0a9ec41b21c7f08a43631cfa215dbd8c88f9fff0ec4880962468219",
      "definitiontxout": 1
    },
    "bestheight": 217796,
    "besttxid": "ae5ec550fb3b7c5c66c0dfed50ed7c5302ed356e225bc2338e9e04456e99d9a6",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iRXE9y35BQfBu4JRTWH6S7fieKTHpJvWyD",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 1000,
      "supply": 2000,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 1000,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 32,
      "name": "PAXG",
      "currencyid": "iPhxTWaHfUWJgzgdyx9qnqExpGqLRaC748",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 546683,
      "endblock": 0,
      "preallocations": [
        {
          "iPhxTWaHfUWJgzgdyx9qnqExpGqLRaC748": 500000
        }
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "810651a7356bf00701a5f5d03cc43e7211d0ecdd",
      "fullyqualifiedname": "PAXG",
      "definitiontxid": "1ce2d089d45ced878f4684010a9468b1ae471c113af470c226edf6dc9aa0be19",
      "definitiontxout": 1
    },
    "bestheight": 546682,
    "besttxid": "3601ecee74c5d4cb875b25b7c2889ae21093a37dbd78cc059603b8d2f8eb30c7",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iPhxTWaHfUWJgzgdyx9qnqExpGqLRaC748",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 500000,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 32,
      "name": "IlikeCoffe",
      "currencyid": "i9fpXvWExEbp6ehTV9t6oYpi6VrgYbzxsK",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 2,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 540571,
      "endblock": 0,
      "preallocations": [
        {
          "i9fpXvWExEbp6ehTV9t6oYpi6VrgYbzxsK": 100000
        }
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "11a20c0ca097d0d8953619c7be0dfad6f59af343",
      "fullyqualifiedname": "IlikeCoffe",
      "definitiontxid": "2abec59242912f4e1338829ccb8c98e8be4d7354d9c529a628127926691b6a1b",
      "definitiontxout": 1
    },
    "bestheight": 540570,
    "besttxid": "032074832b4153ddc10c2b8479c2e1be788ae0c806878188be32266c83402bdf",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "i9fpXvWExEbp6ehTV9t6oYpi6VrgYbzxsK",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 100000,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 40,
      "name": "GOLD",
      "currencyid": "iQP7TeWNDNsF7aaaCkQzNyS4jDjdKncNWf",
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
      "currencyidhex": "b502ec0f3dd6863f54076355fb5c8520d18c54e5",
      "fullyqualifiedname": "GOLD",
      "definitiontxid": "5a98c3f2d73243a8221a07690e07f5722a4e517b7600fbb2d4bcff4422a9711e",
      "definitiontxout": 1
    },
    "bestheight": 149,
    "besttxid": "14bb9f9876145f94a1a144a9a25520d4cebfe194c7a6c585d63baa2737587bb2",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iQP7TeWNDNsF7aaaCkQzNyS4jDjdKncNWf",
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
  },
  {
    "currencydefinition": {
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
      "definitiontxid": "9ea9775f997ff9e24121cec81b3fb9c014c98bfdeb0361e4fd5d9e78fb99e01f",
      "definitiontxout": 1
    },
    "bestheight": 149,
    "besttxid": "75182b9aae64a048d82c55cb8841ab2880c0ca826dee963f2fc89750e4348a6d",
    "besttxout": 1,
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
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 32,
      "name": "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ_Bach123_songs",
      "currencyid": "iN2CDwp2SMrSXJ4ZT1oGUtcpzS3rVHpN11",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 2,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 491008,
      "endblock": 0,
      "preallocations": [
        {
          "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ": 1
        }
      ],
      "idregistrationfees": 0,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "1263285d1f75915402f60fad45f5d152368a6fcb",
      "fullyqualifiedname": "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ_Bach123_songs",
      "definitiontxid": "79603b21fec61319dd47376295c61aad16c9d180eb91608edb5bf5fc61fda520",
      "definitiontxout": 1
    },
    "bestheight": 491007,
    "besttxid": "51a9dccb1b4ba86c0fe52ba2425d567a758f1b7be16bf17916535591113b7624",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iN2CDwp2SMrSXJ4ZT1oGUtcpzS3rVHpN11",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 1,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 33,
      "name": "TRIDENTFINAL2🔱",
      "currencyid": "iDvKAVVHC5G2C4zHVSVkDgi5rFJYdC9hii",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 475125,
      "endblock": 0,
      "currencies": [
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "iDMAoXEjZLkpofokBGsVwen7YEwo1iujMQ",
        "iPJCmjFfPTPSEecRQ4htkaCmJ3C4YWDZHa"
      ],
      "weights": [
        0.25,
        0.5,
        0.25
      ],
      "conversions": [
        0,
        0,
        0
      ],
      "initialsupply": 1000000,
      "prelaunchcarveout": 0,
      "initialcontributions": [
        0,
        0,
        0
      ],
      "idregistrationfees": 1,
      "idreferrallevels": 0,
      "idimportfees": 0.02,
      "currencyidhex": "4e859431921237daf2f7666d960a83b7d9d49172",
      "fullyqualifiedname": "TRIDENTFINAL2🔱",
      "definitiontxid": "592f035be93a5f0db793304d6611c49c76ab7346e39739e071f4706441596522",
      "definitiontxout": 1
    },
    "bestheight": 475124,
    "besttxid": "92ddee6fe02cf0cf0e335256db1422882498987a4b6495dd05e244f50d65a68f",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 37,
      "version": 1,
      "currencyid": "iDvKAVVHC5G2C4zHVSVkDgi5rFJYdC9hii",
      "reservecurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.25,
          "reserves": 0,
          "priceinreserve": 0.25
        },
        {
          "currencyid": "iDMAoXEjZLkpofokBGsVwen7YEwo1iujMQ",
          "weight": 0.5,
          "reserves": 0,
          "priceinreserve": 0.5
        },
        {
          "currencyid": "iPJCmjFfPTPSEecRQ4htkaCmJ3C4YWDZHa",
          "weight": 0.25,
          "reserves": 0,
          "priceinreserve": 0.25
        }
      ],
      "initialsupply": 1000000,
      "emitted": 0,
      "supply": 0,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.000004,
          "viaconversionprice": 0,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.25
        },
        "iDMAoXEjZLkpofokBGsVwen7YEwo1iujMQ": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.000002,
          "viaconversionprice": 0,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.5
        },
        "iPJCmjFfPTPSEecRQ4htkaCmJ3C4YWDZHa": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.000004,
          "viaconversionprice": 0,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.25
        }
      },
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 33,
      "name": "gamesession4",
      "currencyid": "iKZ3UVPdhvcmFuKyeDG4D2MTC3fVj8aNPJ",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 183894,
      "endblock": 0,
      "currencies": [
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "iN9vbHXexEh6GTZ45fRoJGKTQThfbgUwMh"
      ],
      "weights": [
        0.5,
        0.5
      ],
      "conversions": [
        0,
        0
      ],
      "initialsupply": 1,
      "prelaunchcarveout": 0,
      "initialcontributions": [
        0,
        0
      ],
      "idregistrationfees": 0.01,
      "idreferrallevels": 3,
      "idimportfees": 1e-8,
      "currencyidhex": "e4068b940d90a929cd39514979bd0532fdc05cb0",
      "fullyqualifiedname": "gamesession4",
      "definitiontxid": "6f6e77bff28662166d1fe9c2f9c3b7b2d963f79f33a8a76d9c25d715dd545b23",
      "definitiontxout": 1
    },
    "bestheight": 183933,
    "besttxid": "bafce3c8f42a64b6fe39087d9c0599fd25c379f19af4d90f7f37638ef37d2133",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 49,
      "version": 1,
      "currencyid": "iKZ3UVPdhvcmFuKyeDG4D2MTC3fVj8aNPJ",
      "reservecurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.5,
          "reserves": 0.9997485,
          "priceinreserve": 1.98672373
        },
        {
          "currencyid": "iN9vbHXexEh6GTZ45fRoJGKTQThfbgUwMh",
          "weight": 0.5,
          "reserves": 1.57,
          "priceinreserve": 3.11994093
        }
      ],
      "initialsupply": 1,
      "emitted": 0,
      "supply": 1.00642931,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0.00000156,
          "lastconversionprice": 1.99950012,
          "viaconversionprice": 1.95,
          "fees": 0.0002001,
          "conversionfees": 0,
          "priorweights": 0.5
        },
        "iN9vbHXexEh6GTZ45fRoJGKTQThfbgUwMh": {
          "reservein": 0.02,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 3.10997306,
          "viaconversionprice": 3.11993345,
          "fees": 0.000005,
          "conversionfees": 0.000005,
          "priorweights": 0.5
        }
      },
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0.00642931,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 33,
      "name": "CUR",
      "currencyid": "iKSxKeUn6YMDAMZX8ynFx5tZWqXoviuJWB",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 7003,
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
      "initialsupply": 21000,
      "prelaunchcarveout": 0,
      "preallocations": [
        {
          "i7FDrFnMXnTddMar5txtEGQjgG4SKhKR9N": 100
        }
      ],
      "initialcontributions": [
        100
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "2d5f87580a1a6afd4a1840e592858fb5fff435af",
      "fullyqualifiedname": "CUR",
      "definitiontxid": "daf6d9b5b4ba5a871142e552aa66af906b9b8f5e982188b59ec84417794ff025",
      "definitiontxout": 1
    },
    "bestheight": 20158,
    "besttxid": "8f5f15fe566ce54578d926dd5401fa6eabc7a766ec05ee5c2341f7c0bb8df433",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 49,
      "version": 1,
      "currencyid": "iKSxKeUn6YMDAMZX8ynFx5tZWqXoviuJWB",
      "reservecurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.99526066,
          "reserves": 112.51321037,
          "priceinreserve": 0.00476588
        }
      ],
      "initialsupply": 21000,
      "emitted": 0,
      "supply": 23720.45948957,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 49.99375,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.00475963,
          "viaconversionprice": 0.00475963,
          "fees": 0.0127001,
          "conversionfees": 0.0125,
          "priorweights": 0.99526066
        }
      },
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 10502.39199265,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 2080,
      "name": "T10",
      "currencyid": "iGzydSgbgDsysiPoc5hiKyCRVe83CBiLQJ",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 249698,
      "endblock": 0,
      "currencies": [
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq"
      ],
      "conversions": [
        0
      ],
      "maxpreconversion": [
        0
      ],
      "preallocations": [
        {
          "iGzydSgbgDsysiPoc5hiKyCRVe83CBiLQJ": 1e-8
        }
      ],
      "initialcontributions": [
        0
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "c574de9736e5854646b366e33985ba8339fb5b94",
      "fullyqualifiedname": "T10",
      "definitiontxid": "5bc1b469462d5babf4eb3ac2026ee32f54f8dc6a4a699cbe8a39a194b96ab52b",
      "definitiontxout": 1
    },
    "bestheight": 249697,
    "besttxid": "9b087c6e53f6005dacb9e129f8cb541ca46a9457409392e8b6136c9de367fd00",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iGzydSgbgDsysiPoc5hiKyCRVe83CBiLQJ",
      "launchcurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0,
          "reserves": 0,
          "priceinreserve": 0
        }
      ],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 1e-8,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0,
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
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 41,
      "name": "CANADA",
      "currencyid": "iPhvrKgnafcp7PAwZRfHoSHj2DuuYtfMM3",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 547338,
      "endblock": 0,
      "currencies": [
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "iMUw5xvWkC7qsCzgxi2um9YRCmugmBhBfm",
        "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3"
      ],
      "weights": [
        0.34,
        0.33,
        0.33
      ],
      "conversions": [
        0,
        0,
        0
      ],
      "initialsupply": 1867000,
      "prelaunchcarveout": 0,
      "initialcontributions": [
        8047.9125,
        4569780.263,
        0.2399375
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "7f887f4e64f5d69c7d62fbf22c789305b978ebdd",
      "fullyqualifiedname": "CANADA",
      "definitiontxid": "c6507eb0aa3c44fc4f4dcd044b4d370d63e1130209fe0d97462142db5d26712d",
      "definitiontxout": 1
    },
    "bestheight": 547997,
    "besttxid": "f4999ebfd79435f6111e81a0a285fc6de690c2b382bf6ac5baf3ae595afa6eea",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 49,
      "version": 1,
      "currencyid": "iPhvrKgnafcp7PAwZRfHoSHj2DuuYtfMM3",
      "reservecurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.34,
          "reserves": 8046.93927421,
          "priceinreserve": 0.01268421
        },
        {
          "currencyid": "iMUw5xvWkC7qsCzgxi2um9YRCmugmBhBfm",
          "weight": 0.33,
          "reserves": 4563509.47865067,
          "priceinreserve": 7.41133855
        },
        {
          "currencyid": "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3",
          "weight": 0.33,
          "reserves": 0.2401375,
          "priceinreserve": 3.8e-7
        }
      ],
      "initialsupply": 1867000,
      "emitted": 0,
      "supply": 1865900,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 0,
          "primarycurrencyin": 0.125,
          "reserveout": 0.00158467,
          "lastconversionprice": 0.01267736,
          "viaconversionprice": 0.01267736,
          "fees": 0.0002001,
          "conversionfees": 0,
          "priorweights": 0.34
        },
        "iMUw5xvWkC7qsCzgxi2um9YRCmugmBhBfm": {
          "reservein": 0,
          "primarycurrencyin": 999.75,
          "reserveout": 7413.51509776,
          "lastconversionprice": 7.41536894,
          "viaconversionprice": 7.41536894,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.33
        },
        "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 3.8e-7,
          "viaconversionprice": 3.8e-7,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.33
        }
      },
      "primarycurrencyfees": 0.25,
      "primarycurrencyconversionfees": 0.25,
      "primarycurrencyout": -1000,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 58,
      "name": "bambam",
      "currencyid": "iF6hHpRXpmhLq77eksQzqQrWuminKtzmxT",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 258324,
      "endblock": 0,
      "preallocations": [
        {
          "iF6hHpRXpmhLq77eksQzqQrWuminKtzmxT": 727272
        }
      ],
      "idregistrationfees": 27,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "892ac842da88140fb0305e648480899e4396807f",
      "fullyqualifiedname": "bambam",
      "definitiontxid": "d35cd4c6983f4b811e01d066c4cd2ae6cb67008cf9bd1c1ee68ac9bc85441433",
      "definitiontxout": 1
    },
    "bestheight": 270278,
    "besttxid": "19ab5a894437bb73c32ecc133e5a7c890bc16a4405554d9d130aa4f9c912d553",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iF6hHpRXpmhLq77eksQzqQrWuminKtzmxT",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 626945.4,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": -8100,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 32,
      "name": "IlikeTea",
      "currencyid": "iS78r73yrp57ScUjVprCyqUYJW4NXfaHqA",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 2,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 540587,
      "endblock": 0,
      "preallocations": [
        {
          "iS78r73yrp57ScUjVprCyqUYJW4NXfaHqA": 100000
        }
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "afe5b2b419ce7b2839847a8846108c82e14d3ff8",
      "fullyqualifiedname": "IlikeTea",
      "definitiontxid": "befb53884eb6098055d7f14c2bfb812159a2f1fed861af65020d208fc6d4b533",
      "definitiontxout": 1
    },
    "bestheight": 540586,
    "besttxid": "41325ca15d02917442afb103da09152989b24ff1ebd02da7eec1d1789e1b9b07",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iS78r73yrp57ScUjVprCyqUYJW4NXfaHqA",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 100000,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 32,
      "name": "IlikeTea2",
      "currencyid": "i5NSQ4aGC4FJHauNvie5UkCdD51swnRKHQ",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 2,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 541911,
      "endblock": 0,
      "preallocations": [
        {
          "i5NSQ4aGC4FJHauNvie5UkCdD51swnRKHQ": 100000
        }
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "ca16d7c37301146dd40e0da98681e67a928dc914",
      "fullyqualifiedname": "IlikeTea2",
      "definitiontxid": "836004c3dc2992da2993c6412bbc139d5c3437a7db948a178d5b3bebf9f49c35",
      "definitiontxout": 1
    },
    "bestheight": 541910,
    "besttxid": "924166e78ecf58fb1759c1b9e4f7de75e570cea08570232b8c92830fa63f65b7",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "i5NSQ4aGC4FJHauNvie5UkCdD51swnRKHQ",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 100000,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 33,
      "name": "SPORTS",
      "currencyid": "iGhBps9rmbN7U544dZY7nx2rfg26QTh1zY",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 26396,
      "endblock": 0,
      "currencies": [
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "iCMb1B94SWH3g6hFMjcz4J8nav7yF1PHM9",
        "iHCfj1pD1RAfnd2JRhb3KauBpdCmMJoSUA",
        "iRXKBVTVqEPyHrFsUbUW5ahDZRqCWGMTXd",
        "iKnZ2MxxQEzrqw4JwCD3wkVFxh2RDaMFnJ"
      ],
      "weights": [
        0.4,
        0.15,
        0.15,
        0.15,
        0.15
      ],
      "conversions": [
        0,
        0,
        0,
        0,
        0
      ],
      "initialsupply": 78000000,
      "prelaunchcarveout": 0,
      "initialcontributions": [
        640,
        7998000000,
        7998000000,
        7998000000,
        7998000000
      ],
      "idregistrationfees": 5000,
      "idreferrallevels": 0,
      "idimportfees": 0.02,
      "currencyidhex": "eeff130d0c3b438b5c4cd44c78958cbeeeacfe90",
      "fullyqualifiedname": "SPORTS",
      "definitiontxid": "ae4f045146e2b9b8fcd379257a8ee2e96c7becafaf7d0f3a60921d7562eff535",
      "definitiontxout": 1
    },
    "bestheight": 470023,
    "besttxid": "736afe988c89b458a4980d8f87658191d49daabcceccf14f4a1a6731044485e6",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 49,
      "version": 1,
      "currencyid": "iGhBps9rmbN7U544dZY7nx2rfg26QTh1zY",
      "reservecurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.4,
          "reserves": 644.95863898,
          "priceinreserve": 0.00002068
        },
        {
          "currencyid": "iCMb1B94SWH3g6hFMjcz4J8nav7yF1PHM9",
          "weight": 0.15,
          "reserves": 8000000000,
          "priceinreserve": 684.19927303
        },
        {
          "currencyid": "iHCfj1pD1RAfnd2JRhb3KauBpdCmMJoSUA",
          "weight": 0.15,
          "reserves": 7998101217.727316,
          "priceinreserve": 684.03687985
        },
        {
          "currencyid": "iRXKBVTVqEPyHrFsUbUW5ahDZRqCWGMTXd",
          "weight": 0.15,
          "reserves": 7899170791.131446,
          "priceinreserve": 675.57586411
        },
        {
          "currencyid": "iKnZ2MxxQEzrqw4JwCD3wkVFxh2RDaMFnJ",
          "weight": 0.15,
          "reserves": 8000000000,
          "priceinreserve": 684.19927303
        }
      ],
      "initialsupply": 78000000,
      "emitted": 0,
      "supply": 77950000,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 2.99925,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 0.0000206,
          "viaconversionprice": 0.00002064,
          "fees": 0.0017001,
          "conversionfees": 0.0015,
          "priorweights": 0.4
        },
        "iCMb1B94SWH3g6hFMjcz4J8nav7yF1PHM9": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 684.19927303,
          "viaconversionprice": 682.92457425,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.15
        },
        "iHCfj1pD1RAfnd2JRhb3KauBpdCmMJoSUA": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 684.03687985,
          "viaconversionprice": 682.76248361,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.15
        },
        "iRXKBVTVqEPyHrFsUbUW5ahDZRqCWGMTXd": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 98857506.07701468,
          "lastconversionprice": 684.03064333,
          "viaconversionprice": 679.16112229,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.15
        },
        "iKnZ2MxxQEzrqw4JwCD3wkVFxh2RDaMFnJ": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 684.19927303,
          "viaconversionprice": 682.92457425,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.15
        }
      },
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 40,
      "name": "YEN",
      "currencyid": "iAH9uQ4GnREmbpVKd1fU9zrePte3odZGFd",
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
          "i6kcKLQrCAvmajP8LrVxEdPeZajkSjXLvW": 9000000000
        }
      ],
      "initialcontributions": [
        0
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "71717323d3217b1784e0c7033e135e465d55a24a",
      "fullyqualifiedname": "YEN",
      "definitiontxid": "9e3e1f6544ea800e71dc07846b8729db535b52cf3869652d31455fe7592f1636",
      "definitiontxout": 1
    },
    "bestheight": 149,
    "besttxid": "00b7f405d516bb53008846dad3263f87e4fffe701138cfed1833c46a7a21d926",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iAH9uQ4GnREmbpVKd1fU9zrePte3odZGFd",
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
      "supply": 9000000000,
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
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 41,
      "name": "AMERICA",
      "currencyid": "i9c33K8w1ak6iQEYJJvungssTYqtkN5wLQ",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 547317,
      "endblock": 0,
      "currencies": [
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3",
        "iMUw5xvWkC7qsCzgxi2um9YRCmugmBhBfm"
      ],
      "weights": [
        0.34,
        0.33,
        0.33
      ],
      "conversions": [
        0,
        0,
        0
      ],
      "initialsupply": 1776000,
      "prelaunchcarveout": 0,
      "initialcontributions": [
        8117.539,
        0.25,
        4669832.25
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "35e9ea38df2c0a89b79e560163ba2ebcad613c43",
      "fullyqualifiedname": "AMERICA",
      "definitiontxid": "558c2f931326e378ac31fa361fa65f311e50227a0fbd9b30a5d043e7fb3fb438",
      "definitiontxout": 1
    },
    "bestheight": 547994,
    "besttxid": "2191d62da6343a0da23f64f2474345f3d5ae05c0d2ff734bfc95e83af2bf7d59",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 49,
      "version": 1,
      "currencyid": "i9c33K8w1ak6iQEYJJvungssTYqtkN5wLQ",
      "reservecurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.34,
          "reserves": 8116.56632135,
          "priceinreserve": 0.01344991
        },
        {
          "currencyid": "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3",
          "weight": 0.33,
          "reserves": 0.2502,
          "priceinreserve": 4.2e-7
        },
        {
          "currencyid": "iMUw5xvWkC7qsCzgxi2um9YRCmugmBhBfm",
          "weight": 0.33,
          "reserves": 4663036.19557897,
          "priceinreserve": 7.96124441
        }
      ],
      "initialsupply": 1776000,
      "emitted": 0,
      "supply": 1774900,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 0,
          "primarycurrencyin": 0.125,
          "reserveout": 0.00168029,
          "lastconversionprice": 0.01344232,
          "viaconversionprice": 0.01344232,
          "fees": 0.0002001,
          "conversionfees": 0,
          "priorweights": 0.34
        },
        "iBBRjDbPf3wdFpghLotJQ3ESjtPBxn6NS3": {
          "reservein": 0,
          "primarycurrencyin": 0,
          "reserveout": 0,
          "lastconversionprice": 4.2e-7,
          "viaconversionprice": 4.2e-7,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.33
        },
        "iMUw5xvWkC7qsCzgxi2um9YRCmugmBhBfm": {
          "reservein": 0,
          "primarycurrencyin": 999.75,
          "reserveout": 7963.80442103,
          "lastconversionprice": 7.96579587,
          "viaconversionprice": 7.96579587,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.33
        }
      },
      "primarycurrencyfees": 0.25,
      "primarycurrencyconversionfees": 0.25,
      "primarycurrencyout": -1000,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 32,
      "name": "moneybag1",
      "currencyid": "iNxDE8WyJPaRGCpaVDSp5HdvufkorvydzH",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 2,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 553373,
      "endblock": 0,
      "preallocations": [
        {
          "iBN2enGtbojLjemuoa8WET9C3T2GXUWkKd": 1000000
        }
      ],
      "idregistrationfees": 100,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "a65c15feb0ff1e82b9dd4f297990b29ad8d6a6d5",
      "fullyqualifiedname": "moneybag1",
      "definitiontxid": "ab72f29a263975ca7602af3a432d07b2aa01d434e431b240eefb77a6e5b72c3b",
      "definitiontxout": 1
    },
    "bestheight": 554675,
    "besttxid": "0f3f90e8e2bc2205680347fa45ac35f2383aedee1c03c5f04cd5bf17eab16820",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "iNxDE8WyJPaRGCpaVDSp5HdvufkorvydzH",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 999900,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": -100,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 32,
      "name": "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ_my_album",
      "currencyid": "i5GQJSLTPg3CNb7ogKvhDo3vJmQpRCEH7f",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 2,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 486837,
      "endblock": 0,
      "preallocations": [
        {
          "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ": 1
        }
      ],
      "idregistrationfees": 0,
      "idreferrallevels": 3,
      "idimportfees": 0.02,
      "currencyidhex": "d9b1c8f54d5f9419029c8c60e4b868d7884ea513",
      "fullyqualifiedname": "iEFgJoWtLw9V8g21N16WJqWykRQyy462GZ_my_album",
      "definitiontxid": "1a09c08b790627df1421ef24b2ccc5f35907589a53c1b2f8a2ec20aea1bfdc3c",
      "definitiontxout": 1
    },
    "bestheight": 486836,
    "besttxid": "95a4451af7e057f2f92ff879154815005b58315f571c0c4096812ab4b0f40f78",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 48,
      "version": 1,
      "currencyid": "i5GQJSLTPg3CNb7ogKvhDo3vJmQpRCEH7f",
      "launchcurrencies": [],
      "initialsupply": 0,
      "emitted": 0,
      "supply": 1,
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  },
  {
    "currencydefinition": {
      "version": 1,
      "options": 33,
      "name": "gamecurrency",
      "currencyid": "iP6D7QMtPsrQkZDx9y5DsMQEtxDGuCRSoC",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "notarizationprotocol": 1,
      "proofprotocol": 1,
      "launchsystemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "startblock": 161653,
      "endblock": 0,
      "currencies": [
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "iN9vbHXexEh6GTZ45fRoJGKTQThfbgUwMh"
      ],
      "weights": [
        0.5,
        0.5
      ],
      "conversions": [
        0,
        0
      ],
      "initialsupply": 100000,
      "prelaunchcarveout": 0,
      "preallocations": [
        {
          "iGgXBzssRaTCu9MdGCDvkNEx6RuVZgqCVU": 1000
        }
      ],
      "initialcontributions": [
        0,
        0
      ],
      "idregistrationfees": 1,
      "idreferrallevels": 3,
      "idimportfees": 1e-8,
      "currencyidhex": "31acfa133b84f3b6790ceeef20645c7ff3112ad7",
      "fullyqualifiedname": "gamecurrency",
      "definitiontxid": "6d836efa65948767459104536219aefd6ecca7879fdb9770fdebaf57be2af93c",
      "definitiontxout": 1
    },
    "bestheight": 161652,
    "besttxid": "764fd9e47dd03f18f543c67fb8de9f00a74bcc7ef0988c1c75d315a2684e4563",
    "besttxout": 1,
    "bestcurrencystate": {
      "flags": 49,
      "version": 1,
      "currencyid": "iP6D7QMtPsrQkZDx9y5DsMQEtxDGuCRSoC",
      "reservecurrencies": [
        {
          "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "weight": 0.4950495,
          "reserves": 99.97500157,
          "priceinreserve": 0.0019995
        },
        {
          "currencyid": "iN9vbHXexEh6GTZ45fRoJGKTQThfbgUwMh",
          "weight": 0.49504951,
          "reserves": 100,
          "priceinreserve": 0.00199999
        }
      ],
      "initialsupply": 100000,
      "emitted": 0,
      "supply": 101000,
      "currencies": {
        "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": {
          "reservein": 0,
          "primarycurrencyin": 99.975,
          "reserveout": 0,
          "lastconversionprice": 0.0019995,
          "viaconversionprice": 0.0019993,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.4950495
        },
        "iN9vbHXexEh6GTZ45fRoJGKTQThfbgUwMh": {
          "reservein": 0,
          "primarycurrencyin": 99.975,
          "reserveout": 0,
          "lastconversionprice": 0.0019995,
          "viaconversionprice": 0.00199955,
          "fees": 0,
          "conversionfees": 0,
          "priorweights": 0.49504951
        }
      },
      "primarycurrencyfees": 0,
      "primarycurrencyconversionfees": 0,
      "primarycurrencyout": 0,
      "preconvertedout": 0
    }
  }
]

