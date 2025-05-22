listidentities help command followed by examples with outputs:

notes:
- listidentities returns a list of all the ID's in the user's wallet
- this can be used as part of the makeoffer ux, where a user can view all their IDs and have the option to "makeoffer" with any of them


./verus help listidentities

listidentities (includecanspend) (includecansign) (includewatchonly)



Arguments
    "includecanspend"    (bool, optional, default=true)    Include identities for which we can spend/authorize
    "includecansign"     (bool, optional, default=true)    Include identities that we can only sign for but not spend
    "includewatchonly"   (bool, optional, default=false)   Include identities that we can neither sign nor spend, but are either watched or are co-signers with us

Result:

Examples:
> verus listidentities true
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "listidentities", "params": [true] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/



EXAMPLE & RESULTS/OUTPUTS:


./verus listidentities

[
  {
    "identity": {
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
    "blockheight": 467542,
    "txid": "106f360fd9bb7e6b4922f9894c0cfa8fee7712db35e1f1e2299f7415433bdc5c",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
      "version": 3,
      "flags": 0,
      "primaryaddresses": [
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "minimumsignatures": 1,
      "name": "user22",
      "identityaddress": "i5uJfUdEB1GN5aZ5XgMfQVVKCaGcwimG2Q",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "contentmap": {},
      "contentmultimap": {},
      "revocationauthority": "i5uJfUdEB1GN5aZ5XgMfQVVKCaGcwimG2Q",
      "recoveryauthority": "i5uJfUdEB1GN5aZ5XgMfQVVKCaGcwimG2Q",
      "timelock": 0
    },
    "blockheight": 395964,
    "txid": "93f802e605098e6c0c3a73bfb7f695bb0ff6813b35db13b68c3d887819c0b241",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
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
    "blockheight": 467504,
    "txid": "408802a9c50043f22e1b370aefd0c2fd2b0e02b822d39aa0c3e6876de6dd98d1",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
      "version": 3,
      "flags": 0,
      "primaryaddresses": [
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "minimumsignatures": 1,
      "name": "Pear",
      "identityaddress": "i96dJjh7F8qs8LRMFWoPCiR8dWoNrtCLnz",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "contentmap": {},
      "contentmultimap": {},
      "revocationauthority": "i96dJjh7F8qs8LRMFWoPCiR8dWoNrtCLnz",
      "recoveryauthority": "i96dJjh7F8qs8LRMFWoPCiR8dWoNrtCLnz",
      "timelock": 0
    },
    "blockheight": 558331,
    "txid": "2cb7609371693056aa05e1d0f5ff116a6d4f95889ef1c5154d2298e7c7ebd961",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
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
    "blockheight": 467504,
    "txid": "70c216bc23c5bdbe633b6dbba79a5b06861829eb4ed25167d1cc76a33dd478c8",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
      "version": 3,
      "flags": 0,
      "primaryaddresses": [
        "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
      ],
      "minimumsignatures": 1,
      "name": "dev test",
      "identityaddress": "iAR97fkgDvRzKGwodnb6gTWeGTExVqv41e",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "contentmap": {},
      "contentmultimap": {},
      "revocationauthority": "iAR97fkgDvRzKGwodnb6gTWeGTExVqv41e",
      "recoveryauthority": "iAR97fkgDvRzKGwodnb6gTWeGTExVqv41e",
      "timelock": 0
    },
    "blockheight": 449644,
    "txid": "c58cc5b78ad081a2220567cf70e2508ca7910700c03c6c25eac8cbdb15538c02",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
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
    "blockheight": 467503,
    "txid": "e23e636d45e930fe91ddf4e18b3788ccf94784714132880ff4c9bc76effa84cc",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
      "version": 3,
      "flags": 0,
      "primaryaddresses": [
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "minimumsignatures": 1,
      "name": "LoginID",
      "identityaddress": "iCyxjcJsQC7YPiXp3dbLgwL7b8nrLurCpS",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "contentmap": {},
      "contentmultimap": {},
      "revocationauthority": "iCyxjcJsQC7YPiXp3dbLgwL7b8nrLurCpS",
      "recoveryauthority": "iCyxjcJsQC7YPiXp3dbLgwL7b8nrLurCpS",
      "timelock": 0
    },
    "blockheight": 383916,
    "txid": "770b37d8daa0aaa201630d2002bdfb07e98e65623ccb8e705568707db27135d6",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
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
    "blockheight": 467535,
    "txid": "25ed6eec32f8a880c3e79dc86e13e9081bf178b550d2ad9fc2a439990bac93f1",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
      "version": 3,
      "flags": 0,
      "primaryaddresses": [
        "RDyDcLWtYXwGue6ac6eNQo5dtxKv4fF8ss"
      ],
      "minimumsignatures": 1,
      "name": "Dev28",
      "identityaddress": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "contentmap": {},
      "contentmultimap": {},
      "revocationauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
      "recoveryauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
      "timelock": 0
    },
    "blockheight": 199104,
    "txid": "9a41a8d7ba177c8ee4f6b52b21f5e782351da95380eb29f83435df9559229856",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
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
    "blockheight": 467503,
    "txid": "798e99995a7240dbe928926c88940695a02575aa425c84527d24c8a847a00b3e",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
      "version": 3,
      "flags": 5,
      "primaryaddresses": [
        "RLE6gkiAtrMVs9XyMaXtec93fgEycAKigP"
      ],
      "minimumsignatures": 1,
      "name": "pokerplayer",
      "identityaddress": "iNeT5c5yrXQ4aEdQ3z7fwaXSHDV8Cohh4u",
      "parent": "i5cEjwjY6PJro7ra7rBmSw6HWb1m8Xo4uu",
      "systemid": "i5cEjwjY6PJro7ra7rBmSw6HWb1m8Xo4uu",
      "contentmap": {},
      "contentmultimap": {},
      "revocationauthority": "iNeT5c5yrXQ4aEdQ3z7fwaXSHDV8Cohh4u",
      "recoveryauthority": "iNeT5c5yrXQ4aEdQ3z7fwaXSHDV8Cohh4u",
      "timelock": 0
    },
    "blockheight": 396079,
    "txid": "f7cb6a7eee62aae743a3f23b30cd6e5f668217e0df7472f3e0d10e56360ed946",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
      "version": 3,
      "flags": 0,
      "primaryaddresses": [
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "minimumsignatures": 1,
      "name": "AI2",
      "identityaddress": "iQjrxAJrdWbmkAhVfWMA9zEXPen5BrU9AN",
      "parent": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "contentmap": {},
      "contentmultimap": {},
      "revocationauthority": "iDHWc4K7bEFjVQCMuY52B4SD1m72fUTEoX",
      "recoveryauthority": "iHbjFumRBT8nxoQeadcaYzzFdJGnMuQGeL",
      "privateaddress": "zs1acdxwfmcaqk72s0ktjwvj3sp7wrlwyg6qy7elcjq6c4xt937w9z8gvfeq6zqj3p3spdwy4ndt3g",
      "timelock": 0
    },
    "blockheight": 558347,
    "txid": "667f6cb804a31063532882b5a524aa02cd5f0b434ee9c9d194a131fd77b38d3a",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
      "version": 3,
      "flags": 0,
      "primaryaddresses": [
        "RGi75h173LD84tTThCu73B9Dp6rupM5zoz"
      ],
      "minimumsignatures": 1,
      "name": "Pear",
      "identityaddress": "iRJPTKsqhSTvBwsYPV8uD2bptLwkUbV6Kw",
      "parent": "iHBwQo7LUmb7QKKqbsd8Kw9BxdQvgTdK9f",
      "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
      "contentmap": {},
      "contentmultimap": {},
      "revocationauthority": "iRJPTKsqhSTvBwsYPV8uD2bptLwkUbV6Kw",
      "recoveryauthority": "iRJPTKsqhSTvBwsYPV8uD2bptLwkUbV6Kw",
      "timelock": 0
    },
    "blockheight": 558333,
    "txid": "d70f41e29b4c82267bef0b42bfa1dafd6550b7301cccacafea64c102f0f0bd7e",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  },
  {
    "identity": {
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
    "blockheight": 467548,
    "txid": "efc8be1014bb07f271a35500e9cdea02254854e472e6ca32268f3c09094cfda2",
    "status": "active",
    "canspendfor": true,
    "cansignfor": true
  }
]

