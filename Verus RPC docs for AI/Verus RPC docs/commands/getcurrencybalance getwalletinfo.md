getwalletinfo & getcurrencybalance help commands followed by examples with outputs:

notes:
- getwalletinfo can be used to see the "reserve balance" which shows the various currencies in the user's wallet across multiple addresses which can be used to makeoffer in the marketplace
- for this to work in the makeoffer command the "fromaddress" needs to be "*" if the funds are located across multiple addresses
- the reserve balance doesn't show all currencies balances in the wallet but it might be good to display/use
- the other way to see the specific currencies and balance is by looking in a specific address using getcurrencybalance


getwalletinfo

EXAMPLE & RESULT/OUTPUT:

./verus getwalletinfo

{
  "walletversion": 60000,
  "balance": 632.94934759,
  "unlocked_balance": 552.95004759,
  "unconfirmed_balance": 0,
  "immature_balance": 0,
  "eligible_staking_outputs": 176,
  "eligible_staking_balance": 632.94934759,
  "reserve_balance": {
    "Fish.CHIPS777": 100984,
    "gamesession5": 0.0009987,
    "YEN": 100,
    "USD": 91.64538744,
    "Kaiju": 28.16433267
  },
  "txcount": 1664,
  "keypoololdest": 1725431550,
  "keypoolsize": 101,
  "paytxfee": 0.0001,
  "seedfp": "410efbe417c03f81e6863395cdc7a90f3728ee69a001187d17eddedec1be164e"
}



getcurrencybalance

./verus help getcurrencybalance

getcurrencybalance "address" ( minconf ) ( friendlynames ) ( includeshared )

Returns the balance in all currencies of a taddr or zaddr belonging to the node's wallet.

CAUTION: If the wallet has only an incoming viewing key for this address, then spends cannot be
detected, and so the returned balance may be larger than the actual balance.

Arguments:
1. "address"      (string || object) The selected address. It may be a transparent or private address and include z*, R*, and i* wildcards.
                                       If this is an object, it can have "address" and "currency" members, where currency limits currencies shown.
2. minconf          (numeric, optional, default=1) Only include transactions confirmed at least this many times.
3. friendlynames    (boolean, optional, default=true) use friendly names instead of i-addresses.
4. includeshared    (bool, optional, default=false) Include outputs that can also be spent by others

Result:
amount              (numeric) The total amount in VRSCTEST received for this address.

Examples:

The total amount received by address "myaddress"
> verus getcurrencybalance "myaddress"

The total amount received by address "myaddress" at least 5 blocks confirmed
> verus getcurrencybalance "myaddress" 5

As a json rpc call
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getcurrencybalance", "params": ["myaddress", 5] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/



EXAMPLES & RESULTS/OUTPUTS:

./verus getcurrencybalance dev28@

{
  "VRSCTEST": 118.79948194,
  "Fish.CHIPS777": 985,
  "USD": 15
}



./verus getcurrencybalance RGi75h173LD84tTThCu73B9Dp6rupM5zoz

{
  "VRSCTEST": 46.98970227,
  "gamesession5": 0.0009987,
  "USD": 58.4,
  "Kaiju": 28.16433267
}



./verus getcurrencybalance zs1fquzxeqxuzxjh54w9mkz7p3ttf6veeen99rd8mwmrg5f29h2mfz96yn9dvetdfj5yrng6qemyyg

{
  "VRSCTEST": 14.9998
}


