Defining currencies on Verus:  help command and example docs

notes:
- to complete this it takes at least 2 commands:  the first command is definecurrency, and the output from definecurrency includes a "hex" - this hex is used in the second command.  The second command is ./verus sendrawtransaction "hex" which sends the currencydefinition to the chain to be processed.



./verus help definecurrency

definecurrency '{"name": "coinortokenname", ..., "nodes":[{"networkaddress":"identity"},..]}'\
                '({"name": "fractionalgatewayname", ..., })' ({"name": "reserveonename", ..., }) ...

This defines a blockchain currency, either as an independent blockchain, or as a token on this blockchain. It also spends
the identity after which this currency is named and sets a bit indicating that it has a currently active blockchain in its name.

To create a currency of any kind, the identity it is named after must be minted on the blockchain on which the currency is created.
Once a currency is activated for an identity name, the same symbol may not be reused for another currency or blockchain, even
if the identity is transferred, revoked or recovered, unless there is an endblock specified and the currency or blockchain has
deactivated as of that end block.

All funds to start the currency and for initial conversion amounts must be available to spend from the identity with the same
name and ID as the currency being defined.

Arguments
      {
         "options" : n,                  (int,    optional) bits (in hexadecimal):
                                                             1 = FRACTIONAL
                                                             2 = IDRESTRICTED
                                                             4 = IDSTAKING
                                                             8 = IDREFERRALS
                                                             0x10 = IDREFERRALSREQUIRED
                                                             0x20 = TOKEN
                                                             0x40 = RESERVED
                                                             0x100 = IS_PBAAS_CHAIN

         "name" : "xxxx",              (string, required) name of existing identity with no active or pending blockchain
         "idregistrationfees" : "xx.xx", (value, required) price of an identity in native currency
         "idreferrallevels" : n,         (int, required) how many levels ID referrals go back in reward
         "notaries" : "[identity,..]", (list, optional) list of identities that are assigned as chain notaries
         "minnotariesconfirm" : n,       (int, optional) unique notary signatures required to confirm an auto-notarization
         "notarizationreward" : "xx.xx", (value,  required) default VRSC notarization reward total for first billing period
         "proofprotocol" : n,            (int,    optional) if 2, currency can be minted by whoever controls the ID
                                                           1 = PROOF_PBAASMMR - Verus MMR proof, no notaries required
                                                           2 = PROOF_CHAINID - non-native only - currency has centralized control, and
                                                                               can mint/burn & change weights
                                                           3 = PROOF_ETHNOTARIZATION - ETH & PATRICIA TRIE proof (do not attempt without
                                                                                       full understanding + C++, JavaScript & Solidity dev(s))

         "notarizationprotocol" : n,            (int,    optional) if 2, currency can be minted by whoever controls the ID
                                                           1 = PROOF_PBAASMMR - Verus MMR proof, no notaries required
                                                           2 = PROOF_CHAINID - chain ID is sole notary for proof, no evidence required
                                                           3 = PROOF_ETHNOTARIZATION - Ethereum notarization & PATRICIA TRIE proof

         "expiryheight"  : n,            (int,    optional) block height at which the transaction expires, default: curheight + 20
         "startblock"    : n,            (int,    optional) VRSC block must be notarized into block 1 of PBaaS chain, default: expiryheight
         "endblock"      : n,            (int,    optional) chain or currency intended to end life after this height, 0 = no end
         "currencies"    : "["VRSC",..]", (list, optional) reserve currencies backing this chain in equal amounts
         "weights"       : "["xx.xx",..]", (list, optional) the weight of each reserve currency in a fractional currency
         "conversions"   : "["xx.xx",..]", (list, optional) if present, must be same size as currencies. pre-launch conversion ratio overrides
         "minpreconversion" : "["xx.xx",..]", (list, optional) must be same size as currencies. minimum in each currency to launch
         "maxpreconversion" : "["xx.xx",..]", (list, optional) maximum in each currency allowed
         "initialcontributions" : "["xx.xx",..]", (list, optional) initial contribution in each currency
         "prelaunchdiscount" : "xx.xx" (value, optional) for fractional reserve currencies less than 100%, discount on final price at launch
         "initialsupply" : "xx.xx"    (value, required for fractional) supply after conversion of contributions, before preallocation
         "prelaunchcarveout" : "0.xx", (value, optional) identities and % of pre-converted amounts from each reserve currency
         "preallocations" : "[{"identity":xx.xx}..]", (list, optional)  list of identities and amounts from pre-allocation
         "gatewayconvertername" : "name", (string, optional) if this is a PBaaS chain, this names a co-launched gateway converter currency
         "blocktime"          : n, (int, optional) target time in seconds to average between blocks (default 60 seconds)
         "powaveragingwindow" : n, (int, optional) total number of blocks to look back when averaging for DAA (default 45 blocks)
         "notarizationperiod" : n, (int, optional) min period miners/stakers must wait to post new notarization to chain (default 10 min at any blocktime)
         "eras"          : "objarray", (array, optional) data specific to each era, maximum 3
         {
            "reward"     : n,           (int64,  required) native initial block rewards in each period
            "decay"      : n,           (int64,  optional) reward decay for each era
            "halving"    : n,           (int,    optional) halving period for each era
            "eraend"     : n,           (int,    optional) ending block of each era
         }
         "nodes"         : "[obj, ..]", (objectarray, optional) up to 5 nodes that can be used to connect to the blockchain         [{
            "networkaddress" : "ip:port", (string,  optional) internet or other supported address for node
            "nodeidentity" : "name@",  (string, optional) published node identity
         }, .. ]
      }

Result:
{
  "txid" : "transactionid", (string) The transaction id
  "tx"   : "json",          (json)   The transaction decoded as a transaction
  "hex"  : "data"           (string) Raw data for signed transaction
}

Examples:
> verus definecurrency jsondefinition
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "definecurrency", "params": [jsondefinition] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/



DOCUMENTATION WITH EXAMPLES/SAMPLES:

Introduction
Launching currencies on Verus, and any other PBaaS-chain (Public Blockchains as a Service), is better, faster, cheaper and more secure than any EVM-like protocol out there. There is no coding involved.

There are two types of currencies that can be launched with the Verus Protocol. Basket currencies (e.g. liquidity pools) and simple token currencies. Both can be issued decentralized, or centralized with minting and burning capabilities.

When a currency is launched, subIDs can be created from it. SubIDs are powerful objects on Verus (and other PBaaS-blockchains). They are exactly the same as VerusIDs, yet can not launch blockchains or currencies.

#Basket currencies (e.g. liquidity pools)
image-basket-currencies

Basket currencies function like automated market makers (AMMs), they have reserves. A reserve can be any currency or token on the Verus network (also bridged). Have a look at the simplified image. If anyone has currency X or Y, they can convert to the basket currency, or convert from reserve to reserve. If anyone has the basket currency, they can go to currency X or Y. A basket currency can have 1 and up to 10 currencies in its reserves.

The basket currency supply is dynamic, depending on how much is converted to the basket currency (supply minted), or back to its reserve(s) (supply burned).

A basket currency can be 100% backed by its reserves, 5%, or anything in between. This is called the reserve ratio, or the weight. The lower the reserve ratio, the more volatile the currency is when people are converting into or out of the basket currency. The value of the basket currency is directly linked to what is in the reserves and what the reserve ratio is.

When a centralized version of this currency is created, the owner of the rootID can mint currencies into existence, while automatically lowering the reserve ratio. Or they can burn currencies and automatically raise the reserve ratio. Anyone can also just burn the currency at will without raising the reserve ratio.

The conversion fees are incredibly low, 0.025% when converting to and from a basket currency, and 0.05% when converting from reserve to reserve currency. These fees go directly to the worldwide miners and stakers of the protocol, and/or they are accrued into the reserves making the basket currency worth more.

Conversion type	Fee	Fee goes to
Basket currency ↔️ reserve	0.025%	0.0125% added to reserves of the basket currency, 0.0125% to the block reward for miners and stakers
Reserve ↔️ reserve	0.05%	0.025% added to reserves of the basket currency, 0.025% to the block reward for miners and stakers
Because all currency conversions are solved simultaneously inside a block, giving all participants the same price, the protocol is MEV-free (no front-running, back-running, sandwich attacks etc.). The protocol doesn’t have any of the problems EVM-like account-based systems have. Verus DeFi is fair, cheap and has no rent-seekers.

Every(!) currency and token on the Verus network (also mapped ERC-20s!), can be used as reserves for basket currencies. As you might start to understand now — basket currencies are unique currencies that can not be found anywhere else and offer an enormous amount of opportunities for value creation.

#Simple token currencies
Simple token currencies and are just currencies without any reserves. They are not as exciting as the basket currencies, yet still offer much value. With all the parameters that can be added, subIDs created and decentralized crowdfund mechanisms, these currencies can support a lot of use cases that are difficult to do with alternative protocols.

The supply of this type of currency is static when it’s a decentralized version. When it’s a centralized version, the owner of the rootID can mint tokens into existence, and anyone can burn them.

This option is also used to create currencies that are mapped to Ethereum ERC-20s. Which means you can send those ERC-20s over to Verus, or from Verus to the ERC-20. This is made possible with the non-custodial Verus-Ethereum Bridge. You can read more about it here.

And of course, a simple token currency can be one of the reserves in a basket currency.

#Ethereum ERC-20
The Verus-Ethereum Bridge makes it possible for currencies and tokens to be send over to Ethereum, and back to Verus. It is a true non-custodial bridge. All tokens and currencies flowing over the bridge are never in anyone’s custody, and are proven and verified by consensus rules. Everything on the Verus-Ethereum Bridge here.

Any currency and token, on Verus or any other PBaaS-blockchain, can be exported to Ethereum as an ERC-20. They can then be used in the Ethereum ecosystem.

Also, any already existing ERC-20 token can be mapped one-to-one as a Verus currency. Meaning any ERC-20 token can live on the Verus blockchain (or any other PBaaS-chain) and take advantage of all the L1 features.

#Crowdfund mechanisms
All currencies can be launched through decentralized crowdfund mechanisms. Set required minimum levels of worldwide participation in your preferred currencies. If by the start time of your currency or token, minimums are not met, all participants will automatically get a refund of all of their preconversions, less the network fees.

The launch options also provide for maximum participation in one or more currencies, pre-launch discounts, price neutral pre-allocations to select VerusIDs that increase the reserve ratio to issue currencies, similarly price neutral carve-outs of proceeds, and pre-launch discounts for early participants. Using VerusIDs, launches can also include vesting schedules in the pre-allocations as well.


Launch currencies
Need help setting up a currency launch? 🤔

Go to the Verus Discord #pbaas-development channel. The community is happy to assist!(opens new window)

image-currencies-launching

This is what a (simple) currency definition looks like:

./verus -chain=VRSCTEST definecurrency '{
  "name":"MyBrand", 
  "options":32, 
  "proofprotocol":2, 
  "preallocations":[{"Klaus@":100}]
}'
The above command is processed into a HEX, and that HEX is broadcasted to the network. Simultaneously the fees are taken from the rootID (and distributed among the block producers) and after waiting a minimum period of 20 blocks the currency is launched and ready to be used by the worldwide network.

#VerusID namespace
To launch a currency on Verus (and any other PBaaS-chain) a namespace is needed. That namespace is a VerusID. The namespace is the name of the currency (e.g. MyBrand@). That namespace can also have subIDs (e.g. product.MyBrand@, user.MyBrand@). The controller of this VerusID is the only one who can create a currency of that name, and they can only do so once.

On Verus a VerusID registration costs between 20 and 100 VRSC, and the launch of a currency costs 200 VRSC. These costs are always paid in the chain’s native coin (to the worldwide miners and stakers). On other PBaaS-chains these costs can differ since the chain launcher can define its own costs for VerusID registrations and currency launches.

#Defining options
To define a currency, choose options. Then combine these options to whatever the currency needs to be. Just add the numbers together in the currency definition. The currency options are listed below.

Options #	Details
1	The currency has reserves, and can be converted to and from the reserves (option 32 needs to be added). Can have one currency as its reserves, or multiple with up to 10 currencies. This is a “Basket currency” — a currency with a basket of reserves. Such a currency can be launched centralized or decentralized.
2	Only the controlling VerusID (the namespace of the currency, the rootID) can create subIDs.
8	Referrals and discounts are enabled for subID creation.
16	Referrals are required for subID creation.
32	The currency is a simple token currency without any reserves. Such a currency can be launched centralized or decentralized. This option is also used for Ethereum ERC-20 mapped tokens.
2048	A single satoshi (0.00000001) NFT token is created & has tokenized control of the root VerusID. Which means you can send the single satoshi token to other addresses and then they have control of the root VerusID.
Let’s give some examples of combined options:

"options":33 — this launches a basket currency. It is options 1 + 32 combined.
"options":2080 — this launches a single satoshi token that has control of the root VerusID. It is options 32 + 2048 combined.
"options":35 — this launches a basket currency, and only the rootID can create subIDs. It is options 1 + 2 + 32 combined.
#Defining parameters
Next up are the parameters. Choose the parameters wisely to launch a currency that suits any need. Not all parameters are needed or combinable. There are many to go through, so let’s start.

#"proofprotocol"
This parameter defines, among others, if the currency is centralized or decentralized. You can choose 1,2 or 3.

1 is default, which launches a decentralized currency (no need to include this parameter when defining such a currency). When subIDs are created with this option, the registration fees are burned.

2 is for a centralized currency. If it’s a basket currency the rootID can mint and burn supply while automatically lowering and raising the reserve ratio (also anyone can burn supply without lowering the reserve ratio). Or when it’s a simple token currency they can just mint and burn supply. The subID registration fees go to the rootID.

3 is for Ethereum ERC-20 mapped tokens. Read more

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"MyBrand", 
  "options":32, 
  "proofprotocol":2, 
  "preallocations":[{"Klaus@":100}]
}'
☝️ A simple token currency called MyBrand, centralized (the controller of the rootID can mint and burn), and has a preallocation of 100 tokens to Klaus@.

#"currencies"
Here you put the names of the currencies (or just one — it must have VRSC when launched on Verus) that will be in the reserves when it’s a basket currency (options:33).

Or when it’s a simple token currency (options:32), what people convert during the preconversion timeframe will go to the rootID of the currency, as a funding mechanism. In the case of a simple token currency, combine it with "conversions" to determine the preconversion price.

Use up to 10 currencies for this parameter.

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"CommunityX", 
  "options":33, 
  "currencies":["vrsctest","MyBrand","InfluencerCoin"], 
  "minpreconversion":[10,50,10],
  "initialsupply":100
}'
☝️ A basket currency called CommunityX. It needs to get a minimum of 10 VRSCTEST, 50 MyBrand and 10 InfluencerCoin into its reserves within the preconversion time frame to be launched. The initial supply of 100 CommunityX will be distributed among the preconverters.

#"conversions"
Use this parameter when launching a simple token currency. Together with "currencies", it can be used as a funding mechanism for the rootID. This parameter is for the preconversion price. So when doing "conversions":[0.1], it means that for every VRSC the preconverter receives 10 CURRENCY after launch. The converted VRSC goes into the rootID.

People can preconvert to this currency within the preconversion time frame. Define a "startblock", or let the default and minimum time frame play out, which is 20 blocks.

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"CoolBrand",
  "options":32,
  "currencies":["vrsctest"],
  "conversions":[0.1],
  "minpreconversion":[1000]
}'
☝️ This simple token currency is called CoolBrand. During the preconversion time frame people need to convert 1000 VRSCTEST to the rootID. In exchange for that they receive 10.000 CoolBrand. If this minimum amount is not met, the currency will not launch, and everyone who did a preconvert will get their funds back.

#"minpreconversion"
Use this parameter to set a minimum amount of preconversions. The minimum amount of preconversions needs to be met or the currency will not launch and everyone gets their conversions returned, minus the transaction and conversion fees. It works both with basket currencies and simple token currencies.

There is a 0.025% fee taken when preconverting. Take this into consideration when trying to meet the minimum amount of preconversions.

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"CompanyX",
  "options":32,
  "currencies":["vrsctest"],
  "conversions":[2],
  "minpreconversion":[500]
}'
☝️ This simple token currency is called CompanyX. During the preconversion time frame people need to convert at least 500 VRSCTEST to the rootID. In exchange for that they receive 250 CompanyX, or more when more is converted. If this minimum amount is not met, the currency will not launch, and everyone who did a preconvert will get their funds back.

#"maxpreconversion"
Use this parameter to set a maximum amount of preconversions. During the preconversion time frame the amount set can not be exceeded. Everything above this amount will be automatically refunded after the currency is launched.

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"CoinCommunity", 
  "options":33, 
  "currencies":["vrsctest"], 
  "maxpreconversion":[100], 
  "initialsupply":100
}'
☝️ This is a basket currency called CoinCommunity. During the preconversion time frame people can convert VRSCTEST into its reserves for 100 CoinCommunity in return. During the preconversion time frame there can not be more than 100 VRSCTEST converted into its reserves. Whatever is preconverted more will be returned.

#"initialcontributions"
The rootID can contribute some or all of the minimum preconversions directly as part of the currency definition. Use this parameter to make an initial contribution to either the reserves when it’s a basket currency (options:33), or to the rootID when it’s a simple token currency (options:32).

The funds to initially contribute need to be in the rootID when defining the currency. After the preconversion time frame is over and the currency launched, the rootID has received an amount of the launched currency.

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"CommunityBasket", 
  "options":33, 
  "currencies":["vrsctest","CoinCommunity"], 
  "initialcontributions":[10,200], 
  "initialsupply":100, 
  "preallocations":[{"Jane@":100},{"John@":50}]
}'
☝️ This is a basket currency called CommunityBasket. The launcher of the currency wanted to make initial contributions to its reserves. At the moment of broadcasting the currency to the network, there needed to be 210 VRSCTEST and 200 CoinCommunity in the rootID. The initial supply of 100 went to the rootID (if there weren’t any more preconverters). At the same time of the launch, 100 CoinCommunity was minted into Jane@ and 50 into John@, this lowered the reserve ratio of the currency.

#"initialsupply"
A required parameter for basket currencies (options:33). This parameter does not work with simple token currencies. This is the initial supply during the preconversion time frame, before the currency is launched. People preconverting into the reserves receive from this initial supply.

⚠️ IMPORTANT: "initialcontributions" and/or preconversions are required, otherwise the initial supply can not go anywhere and the currency is bricked.

Immediately after the currency is launched, the supply can be larger due to "preallocations".

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"SocialBrand", 
  "options":33, "currencies":["vrsctest"], 
  "initialsupply":500, 
  "preallocations":[{"Max@":1000}]
}'
☝️ This is a basket currency called SocialBrand. People can preconvert VRSCTEST into its reserves and in return they get 500 SocialBrand distributed among them. Immediately after launch Max@ receives 1000 SocialBrand, lowering the reserve ratio of the currency.

#"preallocations"
Use this parameter to receive a chosen amount of funds after the preconversion time frame has passed and the currency is launched. Funds can be directed to VerusIDs and R-addresses. Works with simple token currencies and basket currencies.

When using this parameter with basket currencies, after the preconversion time frame has passed and the currency is launched, the reserve ratio is lowered. This is because new currency has been minted after the initial supply ("initialsupply") is distributed, and nothing was new added into the reserves.

Limit for all currency supplies (10 billion)

10 billion (minus 1 satoshi) with 8 decimal places (9999999999.99999999) is now the recommended absolute limit for all currency supplies, including over time with conversions and extended tail emissions for blockchains.

#"prelaunchcarveout"
Only works with basket currencies (options:33). Use this to redirect a percentage of preconverted reserves to the rootID. After the preconversion time frame has passed and the currency is launched, a percentage of the reserves is taken and redirected to the rootID. This lowers the reserve ratio, making the currency more volatile.

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"BusinessBrand", 
  "options":33, 
  "currencies":["vrsctest"], 
  "initialsupply":100, 
  "prelaunchcarveout":0.1
}'
☝️ This is a basket currency called BusinessBrand. People can preconvert VRSCTEST into its reserves in return for 100 BusinessBrand distributed among them. When the currency is launched, 10% VRSCTEST is taken out of the reserves, into the rootID. This lowers the reserve ratio by 10%.

#"prelaunchdiscount"
Only works with basket currencies (options:33). Use this to give people a discount during the preconversion time frame. After the preconversion time frame and the currency is launched, the conversion price will be higher, depending on what percentage the discount was.

When using this parameter, after the currency is launched, the reserve ratio will be lowered by the discounted percentage.

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"DiscountBrand", 
  "options":33, 
  "currencies":["vrsctest"], 
  "initialsupply":100, 
  "prelaunchdiscount":0.5
}'
☝️ This is a basket currency called DiscountBrand. People can preconvert VRSCTEST into its reserves in return for 100 DiscountBrand distributed among them. Immediately after the launch of the currency, when people want to convert, the price is 50% higher. Also, the reserve ratio is 50% lower because of the prelaunchdiscount.

#"weights"
Only works with basket currencies (options:33). Use this to change the respective weights of the reserves in a basket currency. The total of all weights must equal 1. With a minimum of 0.1, since there can’t be more than 10 reserve currencies in a basket currency.

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"MyBusiness", 
  "options":33, 
  "currencies":["vrsctest","BusinessBrand","DiscountBrand"], 
  "initialsupply":100, 
  "weights":[0.5,0.25,0.25]
}'
☝️ This is a basket currency called MyBusiness. During the preconversion time frame there are various currencies that can be converted into its reserves. They have different weights to them. 0.5 for VRSCTEST, 0.25 for both BusinessBrand and DiscountBrand.

#"startblock"
Use this parameter to define the block height when the currency should be launched. There is a preconversion time frame before the currency is launched. When omitting this parameter it uses a 20 block preconversion time frame before the currency is launched.

The preconversion time frame is always 20 blocks, this can not be less.

⚠️ IMPORTANT: Fill in the absolute block height you want the currency to launch on.

#"endblock"
Endblock can not be defined on basket currencies. It does nothing. It could be set as a signal to software that might use the basket currency.

It can be set on centralized (proofprotcol:2) simple token currencies. When the endblock is reached, it turns the centralized currency into a decentralized one (no more minting and burning capabilities.)

#"idregistrationfees"
Use this parameter to change the costs of registering subIDs under the rootID. The default registration fee is 100. When it’s a decentralized currency the fees are burned (and the basket currency becomes worth more because there is less supply, yet the reserves stay the same), when it’s centralized the fees go to the rootID.

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"InternetCommunity", 
  "options":41, 
  "currencies":["vrsctest"],
  "initialcontributions":[25],
  "initialsupply":5000, 
  "idregistrationfees":1
}'
☝️ The is a basket currency called InternetCommunity with subID referrals enabled. The launcher of the currency wanted to make initial contributions to its reserves. There needs to be 225.0002 VRSCTEST in the rootID at the moment of broadcasting the currency to the network (currency launch fee + initial contributions + txfees). The initial supply of 5000 went to the rootID (if there weren’t any more preconverters). The base fee to register a subID is 1 InternetCommunity.

#"idreferrallevels"
image-referralsID Use this parameter to change the levels of referrals used when registering subIDs. The image above shows the division and distribution of subID registration fees, depending on the chosen level. Minimum is 0 levels, maximum is 5. The default is 3 levels.

To enable referrals, add "options":8 to the currency definition.

Example currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"PremiumAccess", 
  "options":40, 
  "proofprotocol":2, 
  "preallocations":[{"Klaus@":2000}],
  "idregistrationfees":300,
  "idreferrallevels":1
}'
☝️ This is a centralized simple token currency called PremiumAccess. The owner of the rootID can mint and burn tokens at will. It has referrals enabled. When the currency is launched 2000 PremiumAccess go to the Klaus@ VerusID. It costs a 300 PremiumAccess fee to register a subID. These fees go to the rootID because it is a centralized token currency. When someone registers a subID using a referral they pay 200 of which 100 goes to the referred subID, and 100 to the rootID.

#"nativecurrencyid"
Use this parameter for mapped ERC-20 tokens. The parameter includes the Ethereum contract address for the ERC-20. Read more

Need help setting up a currency launch? 🤔

Go to the Verus Discord #pbaas-development channel. The community is happy to assist!(opens new window)

#How to launch
Now you know how to create a currency definition with all its options and parameters. Next up: how to actually use the definition to launch a currency.

Here we use the command-line interface. If you want to use the built-in terminal from Verus Desktop, just replace ./verus -chain=VRSCTEST with run.

Use Verus Testnet first! 👷

Before launching your currency or token on Verus (or any other PBaaS-chain), it is highly recommended to try it out on testnet first.

Let's use this example definition to launch the currency:

./verus -chain=VRSCTEST definecurrency '{
  "name":"MyBrand",
  "options":32, 
  "proofprotocol":2, 
  "preallocations":[{"Influencer@":100}]
}'
Entering the above command into the command-line interface wallet gives a HEX value as output. Take that HEX and do the following command below. ⚠️ IMPORTANT: make sure there are enough funds in the rootID for the currency fee (200.0002 VRSC) and the initial contribution (when in parameters).

./verus -chain=VRSCTEST sendrawtransaction "HEX"
After doing the command above the currency has started, the funds from the rootID are taken, and it takes a minimum of 20 blocks (or startblock) to actually launch it (and if all preconversion goals are met).

During the preconversion time frame and after the launch you can lookup all kinds of information on the currency with the following command:

./verus -chain=VRSCTEST getcurrency "MyBrand"


Launch currency with 1:1 mapping of ERC-20

Defining the currency
To create a currency of a specific name, we need a VerusID of the same name. The controller of this VerusID is the only one who can create a currency of that name, and we can only do so once.

The cost for a VerusID on the Verus is 100 VRSC (or 80 when using a referral). The cost to launch a currency is 200 VRSC. Before launching we need to have enough VRSC in the namespace VerusID.

You can also use a .vETH subID. The cost to register a .vETH subID is an amount of Bridge.vETH (0.01 vETH worth).

In our example we have a namespace MyUSDC with which we want to launch a currency that is mapped to the Ethereum USDC ERC-20 (on Goerli testnet, see contract address (opens new window)).

Below is the command to map a currency 1:1 to an ERC-20 on Ethereum. The address field is the Ethereum smart contract address of the ERC-20 we want to map to.

./verus -chain=VRSCTEST definecurrency '{
    "name":"MyUSDC", 
    "options":32, 
    "systemid":"veth", 
    "parent":"vrsctest", 
    "launchsystemid":"vrsctest", 
    "nativecurrencyid":{
        "type":9, 
        "address":"0x98339D8C260052B7ad81c28c16C0b98420f2B46a"
    },  
    "initialsupply":0, 
    "proofprotocol":3
}'
After we put in the command, we get returned a HEX. We use this HEX to launch the currency on the network. Use the command below to launch the currency:

./verus -chain=VRSCTEST sendrawtransaction "HEX"
Now we have to wait a few blocks for the currency to be available on the network.

#Export to Ethereum
The last step is to export the currency to Ethereum so we can see it there too.


Export currency to Ethereum (as ERC-20)

Any currency on Verus can be exported to Ethereum as an ERC-20. The currency can then be used in the complete Ethereum ecosystem, and on the Verus network. Sending to and from Verus and Ethereum couldn't be easier.

Exporting the currency
Now, let’s export a currency from Verus to Ethereum as an ERC-20 over the non-custodial bridge. We must have enough funds to pay for the export.

The command to export a currency to Ethereum as an ERC-20:

./verus -chain=VRSCTEST sendcurrency "myVerusID@" '[{
    "address":"0x85a7dE2278E52327471e174AeeB280cdFdC6A68a", 
    "currency":"myCurrency", 
    "amount":0, 
    "exportto":"veth", 
    "exportcurrency":true, 
    "feecurrency":"veth"
}]'
Let's break the command down with what you can change.

myVerusID@ is the from- and change-address. Can be a VerusID, R-address or i-address. The fee to pay for the export comes from here, and if you paid too much fees the rest will be returned here.

address You can fill in any ETH-address here, it is actually not important what is here.

currency is the name of the currency you wish to export as an ERC-20. E.g. MyCurrency, MyCurrency.vETH.

#Wait for notarization
After the bridge has been notarized to the blockheight where you have exported the currency, you can choose it from the token dropdown on the Bridge website or add it in Verus Mobile.



