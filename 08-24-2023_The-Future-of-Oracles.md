<h1>the future of oracles — beyond apis in a zk enabled, post-bridge world</h1>

Bear markets are for building. This article will attempt to lay out at least my thoughts on what I’m seeing in the crypto ecosystem. **the following opinions are my own and do not necessarily reflect the thoughts of any other part of tellor (the protocol, the team, etc. )

<b>the past cycle</b>

Overall, we were sort of on point with our prediction in the last cycle. Namely it was ETH centric, definitely EVM centric, with only a few chains popping up that got the lion’s share of usage. The big use case was price feeds and we started to get some cross-chain needs near the end, but overall, if you had an oracle that focused on price feeds for EVM chains, you’d be a great oracle. As usual for me though, I overestimated how many people would actually care about decentralizing their oracle. I was super disappointed that most protocols and dapps being built were pretty much centralized through and through with a little marketing paying credence to our values past.

As far as oracles go, there was a big takeoff in terms of usage, but still probably only a few hundred projects out there that needed an oracle and got any sliver of actual usage. In addition, you had a few projects start charging, but for most of the landscape, oracles were funded by tokens issued by the oracle teams. Again, to be fair, this isn’t any different than the rest of the space, but these aren’t self-sustaining businesses yet and we (as oracles) haven’t even found the theoretical symbiotic relationship that some L1 tokens have where users are buying native tokens to pay for transactions.

<b>the next cycle</b>

Now time to get into the fun stuff. Let’s just lay out some predictions for the next 3–5 years and then I can go into how we can build an oracle that makes sense for it.

trends:

    * regulatory clarity
    * defi will merge with cefi and become way less interesting
    * non-evm, non-blockchain use cases will emerge for oracles
    * we’re moving to a post bridge world
    * middleware (e.g. reading an api) will be handled by a zk proof
    * degen shit will continue to go crazy in the unregulated world

<i>regulatory clarity</i>

It’s finally about here. It probably won’t be perfect and a lot of the crypto world may be off limits to US citizens due to KYC requirements, but stupid stuff will be taken care of. Want to invest in staked ETH on coinbase…done. Want to put it in a lending pool, do validation services, or use your crypto as collateral for a loan? All of this will be able to be done via custodians and registered entities. It will open the crypto world up to brand new customers but at the same time be highly divisive in terms of whether the app is run by institutions or degens. KYC will be a thing for many tokens/apps and it will push some use cases further into the anon/censorship resistant category. The big battle I see over the next 5 years on this front is whether any private or non-KYC’d applications will be allowed on most chains, but the investment contract/ security/ registration nonsense should subside.

<i>defi trends</i>

If you get regulatory clarity, you’ll be able to do all of this stuff using a centralized api. You’ll have big names build centralized projects and you won’t care (or even want) it to be on-chain because all of the liquidity will be locked in an exchange wallet. So what the hell is this for, man? Well it’s for decentralization. This current situation of centralized actors pretending to be decentralized will begin to fade. The system will fragment into regulated/unregulated, but I think the latter will be much smaller than the former even if the vast amount of liquidity on most of the tokens we know today fall into the regulated category. Don’t fret though, there will still be plenty of opportunities, mainly in the trend of global, open financialization. Whether it’s a good thing is for another article, but arbitrary financial borders are coming down.

<i>non-EVM use cases</i>

We can admit it, right now oracles are price feeds and bridges. The latter is less thought of as an “oracle”, and I’ll go over it next, but the first will continue to be a trend; the only change is that price feed/ oracle selection will no longer just be a checklist of “do you support this price on this chain?”. Additionally, parties will use oracles to come to consensus on values outside of on-chain things. Need a global settlement price? A libor alternative? How about consumer metrics or survey data for a new study? These systemically important values are usually created in opaque ways with way too little transparency. The ability to document data collection procedures, maintain a network of credibly neutral respondents/reporters, and mechanisms for parsing and reporting the data can and will be done on-chain.

<i>post bridge world</i>

Bridges are going away. Zk proofs and light clients will connect everything and everyone. I say this and all those VC’s who invested in every new bridge protocol are scoffing, but I’m sure even they would recognize that current bridges are simply multisigs. The truth is that the only trustless bridge is one where you can verify the client state directly. You run a light client bridge and you have a delay/escalation mechanism for forks. Any assets bridged across can have exit mechanisms if applicable, and although it’s slower than the L2 vision, each chain maintains sovereignty. You enable different ecosystems to move as fast as they desire and different security assumptions to arise on each chain, something users will have to pay attention to. Once this happens, we can move to the dream of app chains, a vision where each smart contract function, including oracles, has their own chain. I think the big challenges here are the intricacies of interoperability. Managing the systemic risks that stem from different finality times, fork rules, or security practices in each ecosystem will require some serious forethought by ecosystems. We’ll need to be cognizant as an industry to not move too fast, but I’m mainly just writing this down so I can say “told you so” when no one listens.

<i>the death of the middleware vision</i>

It’s likely that zk proofs will make direct API calls trustless within a smart contract. No oracles necessary. When this happens, a lot of low value use cases will dry up. The idea of a shitcoin price feed for a chain with no users will no longer be a use case for partner hungry oracles. But let’s be honest, just querying APIs was never enough to secure anything and maybe it’s time we admit that. Whether it’s a bad API call, the API changing schema, the exchange itself being manipulated, or countless other errors/statistical anomalies, using just an API (or even just a handful) is a recipe for failure and we’ve all known this. There has to be a subjective layer put in place, and much better data definitions for proving what you actually want to know (e.g. the fair price of an asset).

<i>long live absurdity</i>

First we had BTC, which made sense (mostly). Then came alts. Then NFT’s. Each cycle things had cooler real stuff on the long tail (e.g. ETH or L2s or current zk tech), but the majority of the cycle for retail each time was filled with more and more absurd ideas. Blockchain for supply chain was bad, but we had digital pet rocks selling for seven figures last cycle. I’d like to say it’s going to get better, but it likely won’t. Hamster racing, digital ownership of AI sex bots, scanning your eyeballs to upload your wealth and proof of consciousness to a satellite destined for alien planets….whatever happens I’m betting it will make the last cycle look like we were tradfi. And like always, if you’re actually paying attention and make the claim that none of it makes sense, you’ll be ostracized and looked at as a pariah that just “doesn’t get the future”. So enjoy the ride and pretend you get it so you can go to the cool kid parties.

<p align="center">
    <img src= './pictures/swoards.png' width="800" />
</p>


<b>what this means for oracles</b>

For oracles to succeed, they’re going to have to move beyond the middleware role and do more. They’ll need to be data creators, not merely providers. Think of where the subjectivity and the hard parts are…that’s your bread and butter now. And I’m excited. Oracles will actually compete to create GOOD data, not just “data on-chain”.

<i>price feeds</i>

Oracles will need to set standards for price feeds. They’ll need to do research to be experts on what actually makes a price and what methodology makes sense for each user. They’ll manage robust price feeds with actual definitions, outlier detection, aggregation techniques, flash crash handling, and methods for upgrading this; all without centralized control. This is going to be great for the ecosystem. We’ll finally begin to see settlement prices that are robust. The “fair price” of an asset isn’t and won’t just be a last traded price, and defi applications will get serious about their risk models related to these oracles and how to limit exposure while providing capital efficiency.

<i>data collection</i>

For other data heavy information, oracles will be expected to do some sort of transformation / collection work. Think in the terms of inflation data. Right now oracles just report what someone else calculates (e.g. the CPI from the US government). But inflation is just a survey of prices. Why are we trusting this bottleneck? It makes sense that we’ll move up the stack and oracles themselves will be in charge of collecting the raw data and doing the calculations themselves. This is true decentralized data; collected, analyzed, and distributed in a transparent and permissionless manner. Want information on the housing market? Oracles will work to compete at what a global, decentralized housing index actually is. Want information on inflation, unemployment, salaries, consumer trends….the oracle with the best access and transparent methods for collection will outperform and it’s going to be fun to see oracles begin to compete along these lines.

<i>truly subjective data</i>

Oracles are needed because we need an alternative way to come to consensus on things that are outside the purview of the base layer consensus mechanism. By definition, it’s not programmatic (or else it would just be on-chain). Building these systems to handle the hard subjective stuff is where the use case and future lies. It will be the job of the tellor community to articulate to users what data they need and how to ask the system for it. It’s not “what’s the price of BTC/USD according to the Coinbase api”, it’s “what’s a fair market price for BTC/USD”? The former is fragile, the latter is subjective and hard to define, but what most defi protocols are looking for. Oracles will oversee defining those queries and making sure they get to the root of the users needs.

For specific examples outside of price feeds, I think oracles will be used like decentralized legal systems; writing specifications and best practices for determining outcomes and methodologies for a wide range of subjects. From price feed standards, verifying fork choice rules, sampling data availability, methods for upgrading validator sets, all the way to determining truth about real events, collecting data in a user agnostic way, and even using actual human interactions to verify information.

<i>fallback usage</i>

Additionally, you’ll be used as the fallback for everything. Whether it’s a last resort for a price feed, a decentralized court for a bought vote, or a last resort way to pass an admin key back to a hacked/frozen protocol, my vision is to have oracles add that final subjectivity layer to blockchain. Subjectivity is freedom for L1’s, oracles (if they work properly), can bring that same “social consensus” aspect to any layer of the stack where the user wants it.

<b>philosophy as a differentiator</b>

On a long enough timeline, we all build the same product and everyone in the space ends up with the same technology. Being the first to some zk mechanism or having a new defi primitive is cool for the first five seconds it’s uncopied. After that, its execution and philosophy.

Decentralization matters. Having been in the space for a while, you see tons of projects pop up that have awesome ideas and the tech skills to build them. You get insanely jealous of them, wonder why you’re even here at all since these giga brains got it covered. And then you look at their contracts. They have admin key’s littered throughout, a fully upgradeable contract, and then to put the icing on the cake, the token distribution that controls governance makes US income charts appear egalitarian.

This is why you need a protocol that fits your philosophy. Just having “an oracle” was fine for the last bull market, but with costs decreasing and options increasing, the protocols of the future won’t be built with centralized tech.

These systems are being built to be the credibly neutral systems of the new world. Cryptographically securing that where traditional trust-based systems have failed; avoiding capture, by distribution and multiplication (no one person owns the data, and no one system rules the game). And it’s not a one-time thing. There’s no such thing as “permanently credibly neutral”. As we see with the internet, the dollar, or democracy as a whole, just because something starts as or achieves credible neutrality, doesn’t mean it stays that way. You have to fight for it every step of the way and hope that calm, strong minds prevail in tough times where threats to that neutrality occur.

Tellor is here building the infrastructure we want to see for the vision we believe in. Hope this gives you a little insight into what I’m seeing, but feel free to reach out and would love to expand or discuss any of the points made.