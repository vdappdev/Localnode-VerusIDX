listopenoffers help command followed by examples with outputs:

notes:
- shows all the open offers within this wallet




./verus help listopenoffers

listopenoffers (unexpired) (expired)

Shows offers outstanding in this wallet

Arguments
  unexpired                (bool, optional) default=true, list those offers in the wallet which are not expired
  expired                  (bool, optional) default=true, list those offers in the wallet which are expired

Result
  all open offers





  EXAMPLES & RESULts/OUTPUTS:


  ./verus listopenoffers true false

[
  {
    "expires": 888888,
    "txid": "11e10d0e984432e6fbbd7341868a5acd4cae28e8bbf37c7757fbbc64cd981e39",
    "offer": {
      "type": "cryptocondition",
      "commitmenthash": {
        "version": 1,
        "currencyvalues": {},
        "hash": "0000000000000000000000000000000000000000000000000000000000000000"
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "RGskVWRRgDTf4g53NTdtPVgNJ97kLKKWYr",
        "RJrrCwGU4WNfhugNmpsUHnwtHogGPZSyiy",
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "nativeout": 6
    },
    "for": {
      "type": "cryptocondition",
      "reserveoutput": {
        "version": 1,
        "currencyvalues": {
          "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f": 5000
        }
      },
      "spendableoutput": true,
      "reserve_balance": {
        "Kaiju": 5000
      },
      "reqSigs": 1,
      "addresses": [
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 888888,
    "txid": "7bce4df6f8f92b2875f8a1c72140689b391f09330986ac7c45b20cd00f6b693b",
    "offer": {
      "type": "cryptocondition",
      "commitmenthash": {
        "version": 1,
        "currencyvalues": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 1.6
        },
        "hash": "000000000000000000000000f60039167d4789c6a2dca79020be6a4f1a186727"
      },
      "spendableoutput": false,
      "reserve_balance": {
        "USD": 1.6
      },
      "reqSigs": 1,
      "addresses": [
        "R9cR5yYfXnsqzXyJpP5CvbEuLEmYXXeTFK",
        "RBuQfGhpGqUfFwNqju2Epvj9EoCmWjvFnJ",
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "cryptocondition",
      "reserveoutput": {
        "version": 1,
        "currencyvalues": {
          "iAH9uQ4GnREmbpVKd1fU9zrePte3odZGFd": 5000
        }
      },
      "spendableoutput": true,
      "reserve_balance": {
        "YEN": 5000
      },
      "reqSigs": 1,
      "addresses": [
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 777777,
    "txid": "798e99995a7240dbe928926c88940695a02575aa425c84527d24c8a847a00b3e",
    "offer": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 0,
        "primaryaddresses": [
          "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
        ],
        "minimumsignatures": 1,
        "name": "i made this for you",
        "identityaddress": "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
        "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "contentmap": {},
        "contentmultimap": {},
        "revocationauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "recoveryauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "privateaddress": "zs1kv5zk4kyjuyknqmh6neyand9uewp9h5k0fayxjxah5mmk564d4yxxfqtwwd6atytlrhvyy3dj04",
        "timelock": 380000
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "RUVwk7Wg1QmvBRrKHLA2GBL65wafmeogoW",
        "RPC6wpcoFvKekDZdoAPWMFbzk4RZXkC7gg",
        "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "pubkeyhash",
      "spendableoutput": true,
      "reqSigs": 1,
      "addresses": [
        "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
      ],
      "nativeout": 500
    }
  },
  {
    "expires": 888888,
    "txid": "05e0c7a1fe691201ac928854507dbcc3e75c3ee8f620fda7bee4502ba145c948",
    "offer": {
      "type": "cryptocondition",
      "commitmenthash": {
        "version": 1,
        "currencyvalues": {
          "i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ": 5
        },
        "hash": "000000000000000000000000f60039167d4789c6a2dca79020be6a4f1a186727"
      },
      "spendableoutput": false,
      "reserve_balance": {
        "Fish": 5
      },
      "reqSigs": 1,
      "addresses": [
        "RGskVWRRgDTf4g53NTdtPVgNJ97kLKKWYr",
        "RMfuT5orwwZyMAJSk7hqrQWTEoRunMR6hE",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "cryptocondition",
      "reserveoutput": {
        "version": 1,
        "currencyvalues": {
          "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f": 599
        }
      },
      "spendableoutput": true,
      "reserve_balance": {
        "Kaiju": 599
      },
      "reqSigs": 1,
      "addresses": [
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 8888888,
    "txid": "106f360fd9bb7e6b4922f9894c0cfa8fee7712db35e1f1e2299f7415433bdc5c",
    "offer": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 1,
        "primaryaddresses": [
          "RLE6gkiAtrMVs9XyMaXtec93fgEycAKigP"
        ],
        "minimumsignatures": 1,
        "name": "Fish",
        "identityaddress": "i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ",
        "parent": "i5cEjwjY6PJro7ra7rBmSw6HWb1m8Xo4uu",
        "systemid": "i5cEjwjY6PJro7ra7rBmSw6HWb1m8Xo4uu",
        "contentmap": {},
        "contentmultimap": {},
        "revocationauthority": "i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ",
        "recoveryauthority": "i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ",
        "privateaddress": "zs1mgul578r5q6gye3gkj8dxtn7373hlqzvk5d4gwpzg0uz79c6uudnqq5gv2ch5prlk0gmzmw7k4s",
        "timelock": 0
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "RLuXVYHL7bF5HCZJGdiqFtKZYZunPDHDsv",
        "RGfxCC8ZnNa1BsUfnLL9yxZT1J8VGrSxfv",
        "i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ",
        "i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ",
        "i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 0,
        "primaryaddresses": [
          "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
        ],
        "minimumsignatures": 1,
        "name": "monkins",
        "identityaddress": "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
        "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "contentmap": {},
        "contentmultimap": {
          "i4d7U1aZhmoxZbWx8AVezh6z1YewAnuw3V": [
            {
              "i4GC1YGEVD21afWudGoFJVdnfjJ5XWnCQv": {
                "version": 1,
                "flags": 13,
                "objectdata": "cce0f598889d5e90982ae632f14e95ddf01ccd3ca484128a18ca66b3cd9eac369e80623599f60b32d4bcfe3641f2bea17d33e1f5a0ba0726f95a5446729ab543022970d6bec3eac73b26ceeeb95a0b2b8ace52b5867407eb5bd7c23663647d61cedf8ce45aa9215c248e73ca00a47c4127642e8e00f550239c27392e7a5b71426556bc64711a499c091685e42f4c96c620c224",
                "epk": "8dd7b1e9fea45ce987652311a5910544829c9671607851160f11922c2f501d3a",
                "ivk": "75211661f06070cdbbe068190ff644302a8ddc1ee2f322210d389c0af5483e07"
              }
            }
          ]
        },
        "revocationauthority": "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
        "recoveryauthority": "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
        "timelock": 0
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
        "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
        "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 40000000,
    "txid": "0aebe28ef3e38a3f49c89d2f632ebc062b32c9f6dbef067b6771215ed11ea88c",
    "offer": {
      "type": "cryptocondition",
      "commitmenthash": {
        "version": 1,
        "currencyvalues": {},
        "hash": "0000000000000000000000000000000000000000000000000000000000000000"
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "RA9xGtDYggz5nKtHF3HJbpAYkfcTQ4BEc3",
        "RJrrCwGU4WNfhugNmpsUHnwtHogGPZSyiy",
        "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX"
      ],
      "nativeout": 10
    },
    "for": {
      "type": "cryptocondition",
      "reserveoutput": {
        "version": 1,
        "currencyvalues": {
          "i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ": 1000
        }
      },
      "spendableoutput": true,
      "reserve_balance": {
        "Fish": 1000
      },
      "reqSigs": 1,
      "addresses": [
        "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 888888,
    "txid": "c761f6214e9edfbc3baddfe2f86dcda1893a0d38446661978ad9b68de5941298",
    "offer": {
      "type": "cryptocondition",
      "commitmenthash": {
        "version": 1,
        "currencyvalues": {
          "iKdAxEmSy5zDTsdeuhJLguATiEUdTjE8CB": 1e-8
        },
        "hash": "000000000000000000000000f60039167d4789c6a2dca79020be6a4f1a186727"
      },
      "spendableoutput": false,
      "reserve_balance": {
        "dev36": 1e-8
      },
      "reqSigs": 1,
      "addresses": [
        "RUVwk7Wg1QmvBRrKHLA2GBL65wafmeogoW",
        "RJuE8EkB8xjSRFNqv7HWDW3MPpDruNhVsW",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "cryptocondition",
      "unknown": "",
      "spendableoutput": true,
      "reqSigs": 1,
      "addresses": [
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL"
      ],
      "nativeout": 500
    }
  },
  {
    "expires": 40000000,
    "txid": "832a488e1ea5282825e44e1c016c2b110f31d840abeb191ee8f0e4f0bba8f59e",
    "offer": {
      "type": "cryptocondition",
      "commitmenthash": {
        "version": 1,
        "currencyvalues": {},
        "hash": "0000000000000000000000000000000000000000000000000000000000000000"
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "RRRruUc9MX4mhycSC72Th8JKx1zDno587S",
        "RJrrCwGU4WNfhugNmpsUHnwtHogGPZSyiy",
        "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX"
      ],
      "nativeout": 10
    },
    "for": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 0,
        "primaryaddresses": [
          "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
        ],
        "minimumsignatures": 1,
        "name": "i made this for you",
        "identityaddress": "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
        "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "contentmap": {},
        "contentmultimap": {},
        "revocationauthority": "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
        "recoveryauthority": "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
        "timelock": 0
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
        "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S",
        "iJJ7Ge6eyaqHq7F62kf7vEDYgo1mdtBd4S"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 8888888,
    "txid": "efc8be1014bb07f271a35500e9cdea02254854e472e6ca32268f3c09094cfda2",
    "offer": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 2,
        "primaryaddresses": [
          "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
        ],
        "minimumsignatures": 1,
        "name": "player42",
        "identityaddress": "iSKE3trvjUWqGFziyaoarJe92bzDEJw3uv",
        "parent": "i814vg9MCgn26oypfcvRKMdQPVCmS6P8G7",
        "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "contentmap": {},
        "contentmultimap": {},
        "revocationauthority": "iSKE3trvjUWqGFziyaoarJe92bzDEJw3uv",
        "recoveryauthority": "iSKE3trvjUWqGFziyaoarJe92bzDEJw3uv",
        "privateaddress": "zs1fquzxeqxuzxjh54w9mkz7p3ttf6veeen99rd8mwmrg5f29h2mfz96yn9dvetdfj5yrng6qemyyg",
        "timelock": 50
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "RAoDTQuhFEvpJWccHzuijxdpqheqb3HXnF",
        "RPXgetXGqaqNngn9wjuXi3ELNXkBzWYXvd",
        "iSKE3trvjUWqGFziyaoarJe92bzDEJw3uv",
        "iSKE3trvjUWqGFziyaoarJe92bzDEJw3uv",
        "iSKE3trvjUWqGFziyaoarJe92bzDEJw3uv"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 0,
        "primaryaddresses": [
          "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
        ],
        "minimumsignatures": 1,
        "name": "user49",
        "identityaddress": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
        "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "contentmap": {},
        "contentmultimap": {},
        "revocationauthority": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
        "recoveryauthority": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
        "timelock": 380000
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
        "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
        "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 888888,
    "txid": "42f9ef75cca68bf329ac1096bc6e79da7f237226cd56c0ffae2e7ada9bcbf0c3",
    "offer": {
      "type": "cryptocondition",
      "commitmenthash": {
        "version": 1,
        "currencyvalues": {
          "i4cR8gbSGSPRRgfUHyBzJjrS5pVQC7m2SZ": 10
        },
        "hash": "000000000000000000000000f60039167d4789c6a2dca79020be6a4f1a186727"
      },
      "spendableoutput": false,
      "reserve_balance": {
        "Fish": 10
      },
      "reqSigs": 1,
      "addresses": [
        "RUVwk7Wg1QmvBRrKHLA2GBL65wafmeogoW",
        "RMfuT5orwwZyMAJSk7hqrQWTEoRunMR6hE",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "cryptocondition",
      "unknown": "",
      "spendableoutput": true,
      "reqSigs": 1,
      "addresses": [
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL"
      ],
      "nativeout": 5
    }
  },
  {
    "expires": 777777,
    "txid": "70c216bc23c5bdbe633b6dbba79a5b06861829eb4ed25167d1cc76a33dd478c8",
    "offer": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 0,
        "primaryaddresses": [
          "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
        ],
        "minimumsignatures": 1,
        "name": "user55",
        "identityaddress": "i9HCcMiXxMMB12rDsawGQ6H2GmjrHNQnKd",
        "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "contentmap": {},
        "contentmultimap": {},
        "revocationauthority": "i9HCcMiXxMMB12rDsawGQ6H2GmjrHNQnKd",
        "recoveryauthority": "i9HCcMiXxMMB12rDsawGQ6H2GmjrHNQnKd",
        "timelock": 0
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "RGskVWRRgDTf4g53NTdtPVgNJ97kLKKWYr",
        "RXijTKJ6Ae56bWLtgjoKe71cLzu1yUvWLq",
        "i9HCcMiXxMMB12rDsawGQ6H2GmjrHNQnKd",
        "i9HCcMiXxMMB12rDsawGQ6H2GmjrHNQnKd",
        "i9HCcMiXxMMB12rDsawGQ6H2GmjrHNQnKd"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "cryptocondition",
      "reserveoutput": {
        "version": 1,
        "currencyvalues": {
          "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f": 2
        }
      },
      "spendableoutput": true,
      "reserve_balance": {
        "Kaiju": 2
      },
      "reqSigs": 1,
      "addresses": [
        "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 777777,
    "txid": "e23e636d45e930fe91ddf4e18b3788ccf94784714132880ff4c9bc76effa84cc",
    "offer": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 0,
        "primaryaddresses": [
          "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
        ],
        "minimumsignatures": 1,
        "name": "sendit",
        "identityaddress": "iCyjS3Xbe8JxU8V9Yx6Cd2aMSzyV8CA6Ju",
        "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "contentmap": {},
        "contentmultimap": {},
        "revocationauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "recoveryauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "privateaddress": "zs1acdxwfmcaqk72s0ktjwvj3sp7wrlwyg6qy7elcjq6c4xt937w9z8gvfeq6zqj3p3spdwy4ndt3g",
        "timelock": 0
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "RCcqL3zDPG2i7WVHyJUazzYt61HvpfLV45",
        "R9Lo6RMZezkB2X468KSC9Aiu34vmFtKYeM",
        "iCyjS3Xbe8JxU8V9Yx6Cd2aMSzyV8CA6Ju",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "cryptocondition",
      "reserveoutput": {
        "version": 1,
        "currencyvalues": {
          "iFawzbS99RqGs7J2TNxME1TmmayBGuRkA2": 10000
        }
      },
      "spendableoutput": true,
      "reserve_balance": {
        "USD": 10000
      },
      "reqSigs": 1,
      "addresses": [
        "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 777777,
    "txid": "408802a9c50043f22e1b370aefd0c2fd2b0e02b822d39aa0c3e6876de6dd98d1",
    "offer": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 0,
        "primaryaddresses": [
          "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
        ],
        "minimumsignatures": 1,
        "name": "user49",
        "identityaddress": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
        "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "contentmap": {},
        "contentmultimap": {},
        "revocationauthority": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
        "recoveryauthority": "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
        "timelock": 380000
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "RGskVWRRgDTf4g53NTdtPVgNJ97kLKKWYr",
        "RTMMUHuGc3emae8YtfWkehVKmXK4wTpGiU",
        "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
        "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7",
        "i8gBeTF2fnQ4jqrrs7kDYKLQFXq8mmTPf7"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "cryptocondition",
      "reserveoutput": {
        "version": 1,
        "currencyvalues": {
          "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f": 2000
        }
      },
      "spendableoutput": true,
      "reserve_balance": {
        "Kaiju": 2000
      },
      "reqSigs": 1,
      "addresses": [
        "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 8888888,
    "txid": "25ed6eec32f8a880c3e79dc86e13e9081bf178b550d2ad9fc2a439990bac93f1",
    "offer": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 2,
        "primaryaddresses": [
          "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
        ],
        "minimumsignatures": 1,
        "name": "Dev7",
        "identityaddress": "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX",
        "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "contentmap": {},
        "contentmultimap": {},
        "revocationauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "recoveryauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "privateaddress": "zs1kv5zk4kyjuyknqmh6neyand9uewp9h5k0fayxjxah5mmk564d4yxxfqtwwd6atytlrhvyy3dj04",
        "timelock": 50
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "RLuXVYHL7bF5HCZJGdiqFtKZYZunPDHDsv",
        "RLNUi7KixTW6TpjgTxSUQyiU9i1o11t2E4",
        "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "cryptocondition",
      "identityprimary": {
        "version": 3,
        "flags": 0,
        "primaryaddresses": [
          "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
        ],
        "minimumsignatures": 1,
        "name": "monkins",
        "identityaddress": "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
        "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
        "contentmap": {},
        "contentmultimap": {
          "i4d7U1aZhmoxZbWx8AVezh6z1YewAnuw3V": [
            {
              "i4GC1YGEVD21afWudGoFJVdnfjJ5XWnCQv": {
                "version": 1,
                "flags": 13,
                "objectdata": "cce0f598889d5e90982ae632f14e95ddf01ccd3ca484128a18ca66b3cd9eac369e80623599f60b32d4bcfe3641f2bea17d33e1f5a0ba0726f95a5446729ab543022970d6bec3eac73b26ceeeb95a0b2b8ace52b5867407eb5bd7c23663647d61cedf8ce45aa9215c248e73ca00a47c4127642e8e00f550239c27392e7a5b71426556bc64711a499c091685e42f4c96c620c224",
                "epk": "8dd7b1e9fea45ce987652311a5910544829c9671607851160f11922c2f501d3a",
                "ivk": "75211661f06070cdbbe068190ff644302a8ddc1ee2f322210d389c0af5483e07"
              }
            }
          ]
        },
        "revocationauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "recoveryauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "privateaddress": "zs1kv5zk4kyjuyknqmh6neyand9uewp9h5k0fayxjxah5mmk564d4yxxfqtwwd6atytlrhvyy3dj04",
        "timelock": 0
      },
      "spendableoutput": false,
      "reqSigs": 1,
      "addresses": [
        "iRmBDWNs2WahXDAvS2TEsJyJwwHXhwcs7w",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
        "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL"
      ],
      "nativeout": 0
    }
  },
  {
    "expires": 888888,
    "txid": "0cdb113534dd463db40a2298cd69c0d8eb09086fd45fbd4dd7d6c6fa645b99fc",
    "offer": {
      "type": "cryptocondition",
      "commitmenthash": {
        "version": 1,
        "currencyvalues": {
          "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f": 0.8
        },
        "hash": "000000000000000000000000f60039167d4789c6a2dca79020be6a4f1a186727"
      },
      "spendableoutput": false,
      "reserve_balance": {
        "Kaiju": 0.8
      },
      "reqSigs": 1,
      "addresses": [
        "RUVwk7Wg1QmvBRrKHLA2GBL65wafmeogoW",
        "RLdF3cxsromhH1phbps5odv7Ai9R4QjSUN",
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "nativeout": 0.0001
    },
    "for": {
      "type": "pubkeyhash",
      "spendableoutput": true,
      "reqSigs": 1,
      "addresses": [
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "nativeout": 57
    }
  }
]