getoffers help command followed by examples with outputs:

notes:
- getoffers returns offers and they're organized into different categories
- each offer in getoffers has a txid, this txid is used to populate the takeoffer command for each respective offer
- in the user interface we'll want to display the friendly names not just the i-addresses, for a better user experience



./verus help getoffers

getoffers "currencyorid" (iscurrency) (withtx)

Returns all open offers for a specific currency or ID

Arguments
1. "currencyorid"        (string, required) The currency or ID to check for offers, both sale and purchase
2. "iscurrency"          (bool, optional)   default=false, if false, this looks for ID offers, if true, currencies
3. "withtx"              (bool, optional)   default=false, if true, this returns serialized hex of the exchange transaction for signing

Result:
all available offers for or in the indicated currency or ID are displayed

Examples:
> verus getoffers "currencyorid" (iscurrency)
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getoffers", "params": ["currencyorid" (iscurrency)] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/





EXAMPLES & OUTPUTS/RESULTS:

Searching offers by identity name:


./verus getoffers sendit@

{
  "id_iCyjS3Xbe8JxU8V9Yx6Cd2aMSzyV8CA6Ju_for_currency_iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": [
    {
      "currencyid": "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
      "price": 10000,
      "offer": {
        "offer": {
          "name": "sendit",
          "identityid": "iCyjS3Xbe8JxU8V9Yx6Cd2aMSzyV8CA6Ju",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "accept": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 10000
        },
        "blockexpiry": 777777,
        "txid": "e23e636d45e930fe91ddf4e18b3788ccf94784714132880ff4c9bc76effa84cc"
      }
    }
  ]
}


./verus getoffers fish.chips777@

{
  "id_i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ_for_ids": [
    {
      "identityid": "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
      "price": 0,
      "offer": {
        "offer": {
          "name": "Fish",
          "identityid": "i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ",
          "systemid": "i5cEjwjY6PJro7ra7rBmSw6HWb1m8Xo4uu",
          "original": 0
        },
        "accept": {
          "name": "monkins",
          "identityid": "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 8888888,
        "txid": "106f360fd9bb7e6b4922f9894c0cfa8fee7712db35e1f1e2299f7415433bdc5c"
      }
    }
  ]
}



./verus getoffers player42.gamesession5@

{
  "id_iSKE3trvjUWqGFziyaoarJe92bzDEJw3uv_for_ids": [
    {
      "identityid": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
      "price": 0,
      "offer": {
        "offer": {
          "name": "player42",
          "identityid": "iSKE3trvjUWqGFziyaoarJe92bzDEJw3uv",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "accept": {
          "name": "user49",
          "identityid": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 8888888,
        "txid": "efc8be1014bb07f271a35500e9cdea02254854e472e6ca32268f3c09094cfda2"
      }
    }
  ]
}



./verus getoffers user55@

{
  "id_i9HCcMiXxMMB12rDsawGQ6H2GmjrHNQnKd_for_currency_iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f": [
    {
      "currencyid": "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f",
      "price": 2,
      "offer": {
        "offer": {
          "name": "user55",
          "identityid": "i9HCcMiXxMMB12rDsawGQ6H2GmjrHNQnKd",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "accept": {
          "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f": 2
        },
        "blockexpiry": 777777,
        "txid": "70c216bc23c5bdbe633b6dbba79a5b06861829eb4ed25167d1cc76a33dd478c8"
      }
    }
  ]
}



./verus getoffers user49@

{
  "ids_for_id_i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7": [
    {
      "identityid": "iSKE3trvjUWqGFziyaoarJe92bzDEJw3uv",
      "price": 0,
      "offer": {
        "offer": {
          "name": "player42",
          "identityid": "iSKE3trvjUWqGFziyaoarJe92bzDEJw3uv",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "accept": {
          "name": "user49",
          "identityid": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 8888888,
        "txid": "efc8be1014bb07f271a35500e9cdea02254854e472e6ca32268f3c09094cfda2"
      }
    }
  ],
  "id_i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7_for_currency_iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f": [
    {
      "currencyid": "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f",
      "price": 2000,
      "offer": {
        "offer": {
          "name": "user49",
          "identityid": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "accept": {
          "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f": 2000
        },
        "blockexpiry": 777777,
        "txid": "408802a9c50043f22e1b370aefd0c2fd2b0e02b822d39aa0c3e6876de6dd98d1"
      }
    }
  ]
}



./verus getoffers "i made this for you@"

{
  "currency_iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq_for_id_iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S": [
    {
      "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "price": 500,
      "offer": {
        "offer": {
          "name": "i made this for you",
          "identityid": "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "accept": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 500
        },
        "blockexpiry": 777777,
        "txid": "798e99995a7240dbe928926c88940695a02575aa425c84527d24c8a847a00b3e"
      }
    },
    {
      "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "price": 10,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 10
        },
        "accept": {
          "name": "i made this for you",
          "identityid": "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 40000000,
        "txid": "832a488e1ea5282825e44e1c016c2b110f31d840abeb191ee8f0e4f0bba8f59e"
      }
    }
  ]
}



./verus getoffers dev7@

{
  "id_iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX_for_ids": [
    {
      "identityid": "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
      "price": 0,
      "offer": {
        "offer": {
          "name": "Dev7",
          "identityid": "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "accept": {
          "name": "monkins",
          "identityid": "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 8888888,
        "txid": "25ed6eec32f8a880c3e79dc86e13e9081bf178b550d2ad9fc2a439990bac93f1"
      }
    }
  ]
}





searching offers by currency name:


./verus getoffers vrsctest true

{
  "currency_iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq_for_ids": [
    {
      "identityid": "iNZzqYdmfCPCcVSTBjbPT8Q7rqeFohxATu",
      "price": 1.5,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 1.5
        },
        "accept": {
          "name": "kneipe",
          "identityid": "iNZzqYdmfCPCcVSTBjbPT8Q7rqeFohxATu",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 999999,
        "txid": "1a6d5dd71172c02c825984c77b0ffe2c1234af8823a13be8576f2309eca38ce7"
      }
    },
    {
      "identityid": "iNZzqYdmfCPCcVSTBjbPT8Q7rqeFohxATu",
      "price": 1,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 1
        },
        "accept": {
          "name": "kneipe",
          "identityid": "iNZzqYdmfCPCcVSTBjbPT8Q7rqeFohxATu",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 999999,
        "txid": "5f1b63842be64b6d717a757185d1e6bccb538895d753c4b269e0b3931ff2760e"
      }
    },
    {
      "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
      "price": 14,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 14
        },
        "accept": {
          "name": "dude",
          "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 3333333,
        "txid": "d771b0abeeae6497829cebb9267d725c85a3dd18563528d6399680d4bb9dd0da"
      }
    },
    {
      "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
      "price": 5.5,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 5.5
        },
        "accept": {
          "name": "dude",
          "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 3333333,
        "txid": "2cf12565003e6d4aa582acc7e3bd9700356e47c2c84f46954ef3d74b8ed7bf30"
      }
    },
    {
      "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
      "price": 4.4,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 4.4
        },
        "accept": {
          "name": "dude",
          "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 3333333,
        "txid": "85e5890b620ecac69314f6429237c54790ab20883416a45189ec11858c38a6fd"
      }
    },
    {
      "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
      "price": 3.3,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 3.3
        },
        "accept": {
          "name": "dude",
          "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 3333333,
        "txid": "ab1b92856c3aca76077cb2b6a378d91e8784f0e65753aba9078ff04019ab4f8f"
      }
    },
    {
      "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
      "price": 2.2,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 2.2
        },
        "accept": {
          "name": "dude",
          "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 3333333,
        "txid": "3c0dfd64fa620496868905fe7520fe27e3b57f28ea784d15d54747ab3fa8ef2f"
      }
    },
    {
      "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
      "price": 1.1,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 1.1
        },
        "accept": {
          "name": "dude",
          "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 3333333,
        "txid": "e8f271d6c61133b4db9616a194615eef5674fadc0215e2b760b7cf93d09145a0"
      }
    },
    {
      "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
      "price": 0.0001,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.0001
        },
        "accept": {
          "name": "dude",
          "identityid": "i4YzoP8ZHnh1gNywV9PAT6Yz3AkfXxJmtP",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 3333333,
        "txid": "3d071d29d0ef96a3ca6bc924136cbf361c26ca34b1efa1f872ce52bfa377fc7b"
      }
    }
  ],
  "ids_for_currency_iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": [
    {
      "identityid": "iSiyPgTLkTGu8wktUa8FomHyAsDotnpihB",
      "price": 10,
      "offer": {
        "offer": {
          "name": "Dev14",
          "identityid": "iSiyPgTLkTGu8wktUa8FomHyAsDotnpihB",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "accept": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 10
        },
        "blockexpiry": 300000,
        "txid": "ac2408024543000212211fbf322f0f36925ab1254d70e1fe67add1b56225eca9"
      }
    },
    {
      "identityid": "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX",
      "price": 111,
      "offer": {
        "offer": {
          "name": "dev7",
          "identityid": "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "accept": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 111
        },
        "blockexpiry": 500000,
        "txid": "b4edc618356fa7a5f2288a4b06ecd7c407c4c6dd7c9d1841bf5c0a970b24acd0"
      }
    }
  ],
  "currency_iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq_offers_in_currency_iAH9uQ4GnREmbpVKd1fU9zrePte3odZGFd": [
    {
      "currencyid": "iAH9uQ4GnREmbpVKd1fU9zrePte3odZGFd",
      "price": 10,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 1
        },
        "accept": {
          "iAH9uQ4GnREmbpVKd1fU9zrePte3odZGFd": 10
        },
        "blockexpiry": 3000000,
        "txid": "12e7ffc652c55b55f289290a168ae3ecb5896524524507ecc709a2e943c4b1f9"
      }
    }
  ],
  "currency_iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq_offers_in_currency_iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": [
    {
      "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "price": 0.0001,
      "offer": {
        "offer": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.0001,
          "iN9vbHXexEh6GTZ45fRoJGKTQThfbgUwMh": 4
        },
        "accept": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 1
        },
        "blockexpiry": 400000,
        "txid": "a0e06115280069c0b7794842e5cbf3ef56c3f2e999af76dcf14cf3b306962c4c"
      }
    }
  ],
  "currency_iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq_offers_in_currency_iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": [
    {
      "currencyid": "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
      "price": 7.6923077,
      "offer": {
        "offer": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 5,
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.0001
        },
        "accept": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.65
        },
        "blockexpiry": 500000,
        "txid": "3120f2ba063ac8c0f290b215cc370cb401558a28c00b6d78f477b954aeea66d8"
      }
    },
    {
      "currencyid": "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
      "price": 5,
      "offer": {
        "offer": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 5,
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.0001
        },
        "accept": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 1
        },
        "blockexpiry": 3000000,
        "txid": "94d20f31e6ad3bcbbda96a55bac7e5774803f983b3f0bb4e9d9395d9df9ce591"
      }
    },
    {
      "currencyid": "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2",
      "price": 0.1,
      "offer": {
        "offer": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 10,
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.0001
        },
        "accept": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 100
        },
        "blockexpiry": 3000000,
        "txid": "c928dce4dc71ef51a76e95185afc60f922782f9f069ca7cdfa3082418e7de7d3"
      }
    }
  ]
}



./verus getoffers usd true

{
  "currency_iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2_for_ids": [
    {
      "identityid": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
      "price": 10,
      "offer": {
        "offer": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 10,
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.0001
        },
        "accept": {
          "name": "user49",
          "identityid": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "blockexpiry": 3000000,
        "txid": "905f90d882fe6ce4f5e998b628c5a4334d2d3ee757b49f2670bc14b88c487c9d"
      }
    }
  ],
  "ids_for_currency_iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": [
    {
      "identityid": "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
      "price": 20,
      "offer": {
        "offer": {
          "name": "i made this for you",
          "identityid": "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
          "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
          "original": 1
        },
        "accept": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 20
        },
        "blockexpiry": 3000000,
        "txid": "08a0e5ac77a2243bca4f410d1a168583aa375664731db700d7fe2fd80410f651"
      }
    }
  ],
  "currency_iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq_offers_in_currency_iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": [
    {
      "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "price": 10,
      "offer": {
        "offer": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 10,
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.0001
        },
        "accept": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 100
        },
        "blockexpiry": 3000000,
        "txid": "c928dce4dc71ef51a76e95185afc60f922782f9f069ca7cdfa3082418e7de7d3"
      }
    },
    {
      "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "price": 0.2,
      "offer": {
        "offer": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 5,
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.0001
        },
        "accept": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 1
        },
        "blockexpiry": 3000000,
        "txid": "94d20f31e6ad3bcbbda96a55bac7e5774803f983b3f0bb4e9d9395d9df9ce591"
      }
    },
    {
      "currencyid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "price": 0.13,
      "offer": {
        "offer": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 5,
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.0001
        },
        "accept": {
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.65
        },
        "blockexpiry": 500000,
        "txid": "3120f2ba063ac8c0f290b215cc370cb401558a28c00b6d78f477b954aeea66d8"
      }
    }
  ],
  "currency_iAH9uQ4GnREmbpVKd1fU9zrePte3odZGFd_offers_in_currency_iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": [
    {
      "currencyid": "iAH9uQ4GnREmbpVKd1fU9zrePte3odZGFd",
      "price": 10,
      "offer": {
        "offer": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 10,
          "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq": 0.0001
        },
        "accept": {
          "iAH9uQ4GnREmbpVKd1fU9zrePte3odZGFd": 100
        },
        "blockexpiry": 3000000,
        "txid": "5de5702feaed8ace392c307c549c8ffd390ddb8793d4d7a6b22142a6b4b5300b"
      }
    }
  ]
}