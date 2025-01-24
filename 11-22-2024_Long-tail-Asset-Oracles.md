<h1>Long Tail Asset Oracles For Collateral In Defi</h1>

We all see it.  The number of tokens in the world has exploded.  Whether it’s memecoins, NFTs, real world assets (RWAs), options and futures positions, prediction market tokens, tokenized financial positions (i.e. vaults), and even tokenized other tokens (e.g. LSTs), we love tokens.  

And this is great.

Yet most of DeFi still doesn’t support these new tokens.  Besides DEXs and chains, DeFi is still largely limited to blue chip assets with big CEX listings.  Stablecoins and lending protocols have been around almost as long as tokens but they still severely restrict what can be used as collateral.

The dream is that we have millions of tokens and all of them can be used in any protocol, especially backing a stablecoin or lending it out to borrow any number of different assets.  Protocols realize this too. From Aave to Euler to Compound to countless smaller startups, they’re all working on similar problems with slightly different approaches to get us there, but they’re all still dependent on one thing: Oracles.  

<h3>Collateral in a nutshell</h3>

There are many different kinds of collateral, but we want it all to do the same thing.  

If I give you a token (as collateral), you give me a token to borrow.  The borrowed token can be a stablecoin that your protocol mints, an existing stablecoin, or a different coin altogether.  

To make the system safe, these protocols need one formula to hold:

<ul><i>Value of collateral > value borrowed.</i> </ul>

Usually this is done by converting the value of each of the tokens to its price in dollars.  If at any point, the collateral is worth less than that borrowed, the borrower won’t pay back the loan and your system has lost money.  

It’s the job of the oracle to price the collateral. 

To give a concrete example:

If I have ETH and want to borrow USDC, I deposit $100 worth of ETH into a protocol.  The protocol then gives me $90 worth of USDC (slightly over collateralized as is standard).  

An oracle constantly updates the price of ETH.  If the value of the ETH locked goes down to $95…someone can liquidate the position (e.g. give the protocol back $90 worth of USDC for the $95 worth of ETH), thus saving the protocol with $5 to spare.  

If however, the ETH price drops really fast to where it’s only worth $80, now no one wants it.  The system is “undercollateralized” and broken.  Different projects usually have tokens and pools of capital as insurance in case this happens, but it’s not good.  Ideally the system will catch this before it happens in any form. 

So how to fix it. 

The obvious answer is just to over-collateralize more.  This does work, but now defi is at a huge disadvantage to tradfi.  If you have to put $100 in collateral down for a $50 loan, this is awful.  In fact, a lot of tradfi doesn’t even require any collateral!

So we want to be over-collateralized as little as possible.  Easy, now we just need to know the exact price of the collateral asset at all times.  As soon as it gets close, we’ll liquidate it and be fine.  So fastest oracle possible right? 

Unfortunately, fast oracles are risky because they can be wrong.  API failures happen, flash crashes, flash loans, manipulation, and even smart contract bugs can all cause your oracle to give the wrong price.  

And this doesn’t even mention that the “price” might not be the liquidation price.  Let’s say you have a 10M dollar loan liquidating if ETH drops below $3000.  Who is willing to buy 10M of that coin and put  it in your system for a liquidation reward in ETH that’s falling fast?  That’s a lot of money and if they can’t sell $10M of ETH really fast for a stable asset (e.g. USDC), you’ll probably have to pay a premium.  

<h3> Illiquid assets and oracles</h3>

The big issue for these protocols in choosing collateral: “how do we know that the oracle price is accurate?”  If it’s stale or manipulated, you end up in a bad position.  

And this is the problem with smaller tokens.  

For the big, blue chip tokens, you have CEX listings, hundreds of millions of dollars worth of dex liquidity, and handfuls of quality APIs reporting the price on an aggregate of these exchanges.  

For the newer or smaller assets, it’s a little different. 

The main problem  is that there’s just no liquidity.  There are a lot of consequences that stem from this, but the usual suspects seen are:

  * Only one price source with any volume(almost always just an AMM created by the team)
  * There’s often only 5-6 figures of depth on the AMM
  * All of it is provided by two or three people
  * The AMM is often another chain
  * Often the token distribution itself is such that the team owns the lion’s share
    
For these assets, it’s hard to give them an oracle.  The asset price is clearly controlled by a handful of people, it’s cheap to manipulate by anyone, and it’s certainly dependent on at least one other system (the alternate chain/AMM it’s on).  

<b>Paths forward </b>

“You just don’t get it.  My oracle works”:

To be clear, this isn’t “the oracle problem”.  It’s not a problem of “how” to get data on-chain, it’s a problem of “what”.  There are just no good options not because we don’t know how to read apis on-chain, but that it just isn’t an asset where an accurate price is possible in real time. 

All that said, we’re trailblazers here, so the following is a list of all of the options.  There are tradeoffs, but we feel optimistic about the grand vision and that it definitely is possible to make these assets work as collateral for stablecoins or lending protocols… you’ll just have to be careful.  

<b>The options: </b>

  * Traditional Oracle model
  * The AMM pool
  * A TWAP
  * Oracleless
  * “Fundamental value oracle”
  * Integrated/Altered protocols
  * Limits on volume based on liquidity
  * Hooks into pool with auto liquidations/sales
  * Best/worst prices for buying/liquidating 

<ul>Traditional Oracle model</ul>

<b>Description:</b>  The traditional oracle model is the one most lending protocols and stablecoins use.  It’s the chainlink or other centralized oracle model, where a handful of whitelisted nodes ping a series of APIs (e.g. coingecko, CMC, binance, etc.) and then medianize them into an “official” value.  There is no delay on consumption and no disputes or insurance inherent in the system if the API values are wrong. 

<b>Pros:</b> This method is the easiest to integrate, because it’s just what we use now.  If a protocol wants to just use bluechip assets, or is fine leaving the risk up to the users (e.g. use even though it can be manipulated), then this method can work fine. 

<b>Cons:</b>  The big problem is that it doesn’t work for long tail assets (hence the article).  If there’s no liquidity and/or minimal sources, traditional oracles have no option but to just pull the bad sources and this is exactly what they do. Unless you change how the protocol works (use delays, tightly triggered fallbacks or have pauses with centralized control), there’s little one can do to make these work.  

<ul>The AMM pool</ul>

<b>Description:</b> One option for protocols is to just utilize the current price from the on-chain AMM as the oracle.  This of course assumes an asset with some liquidity on a given AMM on the user’s desired chain. 

<b>Pros:</b> A contract read is very easy to integrate and straightforward to understand.  The price is also what you care about (the price you can liquidate at on your own chain) and it’s also the fastest of all prices available (the current on-chain price, so not dependent on an oracle transaction or the challenges of getting a transaction on-chain). Theoretically, this is the best of all oracle choices.  

<b>Cons:</b>  The big problem is that AMM’s are easy to manipulate.  On-chain liquidity may or may not be very deep or even where the assets main liquidity source is.  If the asset only has thin liquidity on this one pool (which characterizes many small coins), it would represent the price, but it would still be subject to manipulation.  A malicious validator or a flash loan with a liquidation on your lending protocol would be disastrous and potentially costless for an attacker.  Additionally, even if you have a sufficiently liquid DEX for your protocol, liquidity can dry up as time goes on (e.g. what happens if the liquidity goes to another chain or to a CEX), so you need to introduce governance risk so you can update the oracle.  

<ul>A TWAP</ul>

<b>Description:</b>  To counteract manipulability on the AMM pool, protocols can use TWAPs (time-weighted average price).  This means that if an attacker wanted to throw the price, they’d need to do so for multiple blocks, thus severely increasing the cost to change the price. 

<b>Pros:</b>  This is a better way to use AMM oracles and an actually censorship resistant price. It gives protocols zero external dependencies or centralization risks that come with most oracles. 

<b>Cons:</b>  This solution has the main disadvantage that it’s just slower.  If the price dips down 10% in 1 minute, but the protocol uses a 30 minute twap, users could be in trouble if not properly collateralized.   By having an outdated or stale oracle by design, users will need to massively overcollateralize the position.  Also, liquidity can dry up and you may need to change the oracle. 

<ul>Oracleless</ul>

<b>Description:</b>  A common solution for projects is to just use “no oracle”.  Most of the time this means that a protocol will rewrite itself to say that each user will define when they liquidate or don’t liquidate (e.g. more of a p2p lending system).  Sometimes “oracless” just means the protocol owning the AMM pool or having an auction /  orderbook built in.  Unless other protections are put in place, this is no different than an external system, but just may now lead to fragmented liquidity. 

<b>Pros:</b> This can make the protocol safer as it doesn’t rely on a third party price. Like most of the AMM oracles, the lack of dependency is the main benefit.  

<b>Cons:</b>  The UX and fungibility of the positions in your protocol is sacrificed going this route.  Most lending protocols rely on positions that users don’t have to manage the price ratio or self liquidation of.  If positions are not fungible, there can be limited liquidity at prices that borrowers want and making stablecoins out of this will usually result in softer pegs (less tightly tied to the target).  

<ul>“Fundamental Value Oracle”</ul>

<b>Description:</b>  For this oracle, protocols could use what “should” be the price.  This will only work for certain instruments, but imagine an LST or LRT; since it represents a locked asset with some conversion factor, one could just use the price of that locked asset as its price.  So for an ETH LST, you can just use the price of ETH (which is robust), multiply by the conversion factor in the contract, and then you don’t have to use an LST price (which will likely only be traded on one or two dexes). You can also do this with derivatives contracts (e.g. run a black scholes model on an options vault) or on prediction market tokens as well (if there’s a “yes/no” market in the off-chain world, you can peg the decentralized oracle to this one). 

<b>Pros:</b> You can use more liquid assets and metrics to peg the value to something stable. Even if the asset you’re using has no liquidity on a dex, you can still find a price for it and use it as collateral. 

<b>Cons:</b>  If there’s a tail risk event (large movement that nullifies the link between the asset and its underlying), the protocol is broken.  An example could be a contract bug in an LST or a regulatory event that causes a discrepancy between the on-chain vs off-chain price. There is also a liquidity risk in that if your contract needs this collateral liquidated, there needs to be a market for it or a way to unwind the position. For some things this is practical (e.g. an LST can be redeemed), but for other things like RWA’s or vaults with certain lock periods, there may be a substantial liquidity premium your liquidators will require. 

<i>Integrated / Altered Protocols</i>
This is the real solution long term.  We’re going to need custom protocols that don’t abstract away risks or pretend that oracles are, or can be, real time. 

There’s a few ways to do this, but some with promise include:

  * Limits on volume based on liquidity
  * Hooks into pool with auto liquidations/sales
  * Best/worst prices for buying/liquidating (use a mix of fast and slow oracles for caution)
  * Systems need to ensure liquidity to liquidate the underlying collateral. 

This is the only method that will work long term. Pooling for tail systemic risks lead to system failures.  Individual users taking on the risk leads to centralization issues with regard to the protocol (e.g. we end up with two insurance firms covering losses and determining payouts).  We need to ensure that systems in web3 are always safe and can be used trustlessly without governance or centralized third party dependencies.

<b>Conclusion</b>

Defi is really hard if you want to use unique collateral.  That said, it’s not impossible.  There are tradeoffs, but if we’re going to build the decentralized dream of being able to tokenize all forms of value, we’re going to need to use any collateral in our system primitives.  Hopefully this article gives you some options and some of the tradeoffs you’ll need to discuss before building your protocol or looking to get your asset included as collateral somewhere.  

For general best practices on oracle integration, check out:  https://tellor.io/blog/using-tellor-best-practices-part-1-development/  

If you’re looking for integration or just want to chat oracles, feel free to reach out to Tellor:  info@tellor.io or join our Discord.  

<b>Further research</b>

Toxic Liquidation Spirals – https://www.academia.edu/99581099/Toxic_Liquidation_Spirals

TWAP and AMM oracle manipulation – https://eprint.iacr.org/2022/445 

Self liquidating lending protocols – https://github.com/hoyu-io/core 

Enshrined Oracles – https://mirror.xyz/themandalore.eth/mvjyNV7vhqrwgT8Xe6FVJYS8KxGsAcyS6y4M23z31K0 
