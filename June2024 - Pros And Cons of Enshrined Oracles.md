<h1>pros and cons of enshrined oracles</h1>

<i>First Published - June 21st, 2024</i>

With the advent of app chains and restaking, the design space for chains is taking off and the idea of having your validators do more is back on the table. One of the ideas that continues to resurface is the concept that your validator/sequencer could be an oracle.   This article aims to describe the option and lay out the pros and cons of going with this approach, finishing with some potential best practices you can follow to ensure a secure chain as well as a robust oracle.

<b>wait, what are we talking about?</b>

The idea of an “enshrined” oracle has been discussed for years, with implementations as early as Amoveo in 2018, and even making its way to a proposal for Ethereum back in 2020.  An example would be all of the validators of a chain signing a median of API calls before each block to update a price variable they make accessible to smart contracts. For a rollup, this could just be the sequencer updating a precompiled contract with the prices of various assets.  For a PoW chain or based rollup (e.g. blocks and transactions arranged on a DA layer), it could just be block proposer entering a value with their block.

sample enshrined oracle where validators tack on oracle data while signing a block
sample enshrined oracle where validators tack on oracle data while signing a block
And that’s kind of it.  Of course you can use it for simple things like prices, but this enshrinement can be used for other types of data too.  Things such as bridges (e.g. posting another chain's block header),  input of real world data like sports feeds, news events, and certain RWAs, or even custom APIs and software results like the ability to query chatGPT from your smart contracts can all be enabled through leveraging your existing validator set.

It’s actually simple in concept,  but as with anything, tradeoffs exist and there are reasons it’s not yet commonplace.

<b>pros</b>

<i>unlimited security</i>

One of the biggest drawbacks of any traditional decentralized oracle system is that they fallback upon their own market cap to secure the data feed.

Take for instance an oracle design where parties stake and can then report data.  If they lie, they get slashed subject to a vote of token holders on whether the submitted data was correct.  This is the traditional way of grabbing outside data.  However, there are three main issues here:


  * Security limit equal to half of market cap

  * Bribing attacks

  * Parasitic attacks

For any decentralized oracle that relies solely on token voting, if you have a token worth 10M dollars, you can’t secure (at least in a crypto-economic sense) an app worth 1B.  The risk is that a majority of your stake will be purchased and then used to break the underlying protocol. In our example, you would only need to purchase 5M and 1 dollars to break the system.

The second issue is a follow up to this.  What prevents someone from launching a bribe contract that says you’ll split the pot of the attacked protocol?  And what if they add in money of their own (e.g. a competitor opens a short position)?  When you look at large stablecoins or lending protocols that need a decentralized price feed, market caps are never enough to secure the dream of trillions of dollars in these systems, especially with a deeper pocketed tradfi competitor that might stand to profit from a broken system.

Lastly, a parasitic attack is when someone uses the oracle but doesn’t pay for it.  If you can only secure $5M due to your market cap, but a non-paying customer uses your oracle to secure their $5M protocol also, you’re now in a bad situation and it’s hard to fix or even know when you’re in this situation.

We’ve known of these issues for years and this is why reputational stakes / whitelists are usually added to fix these systems (e.g. current Chainlink type designs).

Enshrined oracles fix this problem.  Now instead of being secured by an external token, the oracle now has the exact same security guarantee as the chain itself.  This is an attractive proposal because most L1’s (or sovereign L2’s) don’t even have security caps as they have the ability to fork, if their validator set is compromised.

This is a super power of sovereign chains.  Now you can add that security to oracles through your own social layer.

<i>no trusted third party</i>

When using an enshrined oracle  you don’t have to worry about a third party system being compromised, because it’s literally your system. The security is the chain’s security and there’s no one else you need to keep an eye on.  This is powerful even when compared to an oracle that is theoretically large enough to secure your chain.

Issues have arisen in the past where third party oracle providers stop reporting data (either due to low liquidity on a pair or just software bugs for their system).  Without an ability to upgrade the oracle system, you’re at the mercy of the third party, who may not care about your system (smaller users on your chain tend to get cut off).

An enshrined system ensures that you’ll always have the data you need for your chain’s applications and you won’t be subject to third party dependencies.

<i>blazing fast,  perfect connection</i>

One of the biggest issues for most oracles is speed.  Whether you’re a price feed, a bridge, or a cross-chain transaction, you want it to be instantaneous.  Now with an enshrined oracle, the oracle is exactly as fast as your chain.  There’s no more missing a block, no more gas costs to update, or missing a submission because a builder is censoring the transaction.  This is probably one of the biggest selling points for developers and makes using an oracle as seamless as you’d hope for. You just read prices and they’re always up to date.

more control - your governance owns the definitions and priority of transactions

One of the biggest benefits here is that you as the chain own the data. Coming to agreement on what good data looks like is on your consensus mechanism.  If you don’t like it, it’s due to your software and it’s within your ability to fix it.  If you need an oracle for your own token, you don’t need to wait on a third party or pay for an integration with another third party oracle. Additionally you can even specify when oracle updates happen, where in the block they appear, and countless other customizations that are difficult to achieve without running the oracle for yourself.  The design space is honestly just being explored and everyone can see the possibilities.

<b>cons</b>

<i>adds Governance - what to enshrine</i>

The first question is what are you enshrining?  Are you enshrining the ability of your smart contracts to make api calls?  No one does this…lots of risks here.  Are you enshrining a list of API’s?  A price feed is the most common answer, but then it gets tough as to figuring out which prices.  What exchanges do you use?  Do you use paid API’s?  What’s the process for updating this list? These aren’t deal breakers, but these will be your chain’s discussions now.

As someone who runs an oracle, the usual discussion is this:  “I need an XYZ/USD feed up on mainnet as soon as humanly possible.  XYZ just launched, so I have no idea where XYZ trades and I don’t have too much money to pay for it”. Do you add the feed?

It’s tough, but this is what a lot of protocols use as their feeds. They’re thin markets with little history, often with only one (maybe two) endpoints for querying the information.  Either you have a way to add the feed quickly, or you risk losing the business to another protocol. Now you either need to accept it or have a way to charge for these updates.  If you add everything, you can bloat the chain, but adding nothing will limit your system.

Enshrining can work if it’s a small set of feeds that’s known, but it can be chaotic if you’re relying on chain governance to manage relative resource pricing and risk management of feeds.

<i>adds liveness risk - does your chain halt in cases of disagreement</i>

Oracles are hard for a reason. By definition, they’re used for things that you can’t objectively prove.  You need a layer for handling subjective truth.  From the idea of a true price, picking the fork of an alternate chain, or even determining the outcome of a prediction market, the truth is not always apparent.

To take the most common example of price feeds, imagine a scenario where you need the BTC/USD price.  Everything’s working fine, but then a flash crash on Coinbase sends off-chain US prices quickly downard by 20%.  Binance and on-chain dex’s however are not moving.  What price do you input?

If you use a median of API’s, you may be ok…or not.  Maybe you use Kraken, Coinbase, and Binance…now you have a US price.  Maybe the Coinbase API goes down.  What if Bitcoin forks and Binance chooses one fork and Coinbase the other… There’s a whole slew of issues that could arise, but the question for you is what happens to your chain.

Do you halt the chain if the API’s go down?  If you do put in the US price and it walks itself back (e.g. flashes back up bc it was an error), do you fork your chain and revert the price history?

And this doesn’t even get into the slashing aspect.  Is the oracle something you would slash validators over?  And what is a slashable offense?  1% off…5%...  What if the API moves 20% in the time of a block?  What if the validator picks the most advantageous price they see in the timeframe of a block?  Are there inactivity leaks for not submitting a price? These are hard problems with trade-offs either way.

You can use non-specific queries (e.g. we want a valid BTC price), however this has tradeoffs too.  Non-specificity is good if you have an active dispute system, however relying on a social layer to agree upon what is or is not a good price can be difficult.  BTC/USD for instance can vary by several percentage points depending on the CEX; however this difference can cause massive liquidations in a defi protocol.  Being able to be specific in the source is very important for certain applications and  relying on a social layer  is tough to enforce for all but the most egregious of violations.  A validator could be wrong for quite some time and leaning this much on the social layer for decisions that could be routine (e.g. what list of API’s to use or what a good price should be), might end up more of an extractive exploit than a feature to tout.

<i>adds upgrades / maintenance</i>

Adding lots of upgrades and maintenance is bad.  Whether it’s updating an API list, adding new oracles, or handling errors, the more governance you put in place, the more likely each validator will just start blindly following what developers put out.  The idea of competing clients and different software gets much harder.  The forums and github which put forth the upgrades must be vigilantly monitored and it’s not a good thing.   If you’re going to outsource the maintenance and development of these oracles to a third party, just admit the third party dependency and design it differently than just saying it’s on the validators.

<i>increases validator requirements</i>

One of the biggest downsides of enshrining anything is that it increases your validator/ node requirements.   Even if you don’t get into the costs of API keys and VPN’s for grabbing the data, the more data that is added per block, the larger your chain and the faster you’re growing.  This can be fine if oracle updates are part of normal transactions as they pay gas, however resource pricing is difficult in enshrined cases.  You need to monitor how many prices you’re adding and what size or cost challenges it may be imposing on your validator set.

<b>best practices and other options</b>

<i>stay cognizant of the trade-offs</i>

For best practices, the number one thing you can do is just admit the tradeoffs.  Know that you likely won’t be able to add everything.  There will be pairs that have too low of liquidity and you’ll have to constantly monitor api’s and volume to make sure that you don’t fall into a trap of needing to fork your chain to rescue a broken pair.

<i>specify fork choice rules carefully</i>

Make sure you talk about forking.  If you grow and add more things, the conversation will need to happen.  Specifying penalties for inactivity, wrong prices (e.g. Is 1% off ok, is 10%), or failure to update software should be known well ahead of time.  Additionally, you should discuss how you deal with geo-restrictions of certain API’s / data sources well before it actually becomes an issue.  Decentralization is hard and a social/governance layer is necessary to be actually secure, but leaning into your social layer should be done carefully and intelligently.

<i>option - enshrining connection to an oracle layer</i>

One solution would connect your chain to an oracle on another chain.  Whether it’s a purpose built oracle chain like Tellor or just a smart contract system on another chain, your validators could simply enable reads to that system.  This would make it so you still have a connection to the oracle network, but you don’t have to handle data sources, resource pricing, or even disputes of the oracle.  The only thing your chain would need to worry about is validating the blocks of the chain you're connecting to, which is a much lighter weight pull for your social layer (you only have to step in if the oracle network fails).  This solution is particularly attractive for systems that run at block speeds slower than the oracle chain.  If you need subsecond updates of price feeds however, the latency of consensus on another network could be a deal breaker.

<i>option - enabling forking on top of traditional oracles</i>

One possible solution to current oracle limitations is to just tell them that you’ll use your own social layer to make sure they succeed.  This means you could use a centralized oracle like Chainlink/Pyth or a crypto-economic oracle like Tellor/UMA, but then add validator checks that would allow them to halt the oracle if a bad value is detected and potentially fork the chain if needed. Again, depending on how specific your chain is, if the oracle and validation is tightly tied in with the app, even just enabling a fully centralized third party to run it could be ok if you manage the success and exit-ability with your social layer. If the attackers know that forks will revert bad oracle updates, even just the statement will deter oracle attacks on your network.

<i>option - third party to manage oracle feeds for validators</i>

This model has you using your validators as oracles (e.g. updating every block within the construction), but does this by leveraging a third party for maintenance and resource pricing. Just be aware that if you know you’re relying on a third party to pick feeds and pick API’s, you should just keep tabs on where you might need the social layer to step in and where your dependencies lie.  As with the previous option for leveraging third parties, you do rely more on monitoring for bad values, but be sure to have back up plans in case of liveness failures of the third party as well as documentation on how to determine/ build good data for each source (e.g. what’s a good price?  How long do you wait for finality on cross-chain calls?)

<b>Conclusion</b>

The enshrinement of oracles represents an exciting new research path for chains looking to push the boundaries in terms of usability, speed, and security of off-chain data.  As with anything in crypto, there are tradeoffs and it’s ultimately a conversation that depends on specifics of a given chain and application.  To recap and highlight a few features that tend to make enshrinement a bit easier:

  
  * Limited data points - having your validators provide a price for your own native asset and maybe a bridge to a partner chain is different than opening the validator set up for custom oracle queries.  By keeping it limited, you prevent governance risks and limit the scope of what’s on the table for validator requirements.

  * Application specific chain - The more general purpose your chain, the less likely it is you’ll be able to be an oracle for every requested data point.  Additionally, relying on the social layer for resource pricing and development of these updates could be a heavy lift if you expect large numbers of data types and/or sources.

  * Smaller, frequently updated validator set - Any chain and community enshrining their oracle will need to be actively monitoring the API set and the list of assets you provide an oracle service for.  Applications or chains that have more sophisticated validators that can accept this kind of workload and still manage updates will be able to better handle the day-to-day operation and monitoring of an oracle.
  * Transparent and easily apparent correctness of data - As with the first characteristic, updating cross-chain data from large chains, getting price updates on large pairs, or even just doing your own native token has far less risk than connecting or reading from low-liquidity pairs, shoddy API’s, or chains that may fork.  This is a problem for any oracle system, but with a third party application, at least your chain is not dependent on these chokepoints. Be wary of adding new data points that don't have specific definitions and multiple sources for what your community considers “good” data.

The enshrinement of oracles and bridges is here.  As we move towards a world of thousands of chains, we will see countless experiments in terms of leveraging the validator set to do more.  Hopefully this article can serve as a guide and a great starting point for projects beginning this journey.



<b>links for reference/further information:</b>

Vitalik on Overloading consensus: https://vitalik.eth.limo/general/2023/05/21/dont_overload.html

dydx: https://github.com/dydxprotocol

Skip: https://skip.money/

Tellor: https://github.com/tellor-io/layer

E-oracle (restaking) - https://ethresear.ch/t/the-end-game-for-oracles/19276

forkable L2: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4652207

Connor O’hara on subjectivity oracles:  https://www.youtube.com/watch?v=CBHufEP8F4U
