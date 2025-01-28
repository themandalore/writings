<h1> Eigenlayer — crypto rehypothecation and the infinite trust machine</h1>

<p align="center">
    <img src= './pictures/matrix.png' width="800" />
</p>

For the last few months, I’ve had the privilege of being asked my opinion on Eigenlayer, the new hotness when it comes bootstrapping trust networks and building things like oracles and bridges. I’ve been semi-quiet about it so far, but I’ll kick it off strong and put down in writing the arguments I have for and against eigenlayer and why I see it as a pretty lackluster ideal for the space.[1] That said, much dumber and more inefficient ideas have taken off in crypto, so hopefully they can take some of the criticism (with their boatloads of cash[2]), and work to build something that can actually decentralize and secure the space.

<b>What is eigenlayer?</b>[3]

To quote them, eigenlayer is a “restaking” protocol. This means that you take staked ETH (or stake it through them) and deposit it into their protocol. Then these ETH validators who deposited staked ETH can opt-in to also be validators for your “strategy”, be it an oracle, sequencer, data availability layer, etc.

To give an example, Salma’s Stablecoin (SS) needs an SS/USD price feed to peg to. Uniswap oracles suck and she hadn’t heard of tellor, so she decides to build the SS Oracle using eigenlayer and set sail with a secure price feed. The way it works is simple, you stake stETH in the eigenlayer contract and then you can be a signer for the price feed. Then the signers, in addition to signing their ETH blocks, also sign off on the price of SS/USD with each block. Now (or so Eigenlayer would say), you have a robust, fast, and decentralized oracle network made up of the validators of ETH themselves, so there’s no additional trust assumptions.

<b>Why this could be cool</b>

The hardest part of doing any decentralized system is setting up the “trust network”, aka the decentralized nodes and validators running the system. Even if you do have a good idea, it’s insanely difficult to get a sufficient number of globally distributed validators to even be theoretically decentralized. It’s a huge problem and bootstrapping this network (even with inflationary rewards) is super difficult. The Eigenlayer solution is that instead of needing to roll your own, how about you just use Ethereum’s!? It’s the best of both worlds and has been talked about in the past.

In the example for instance, enshrining oracles into the validator’s consensus mechanism has always been a “what if” by vitalik and other giga brains[4]. In fact bridges, or “native bridges” specifically, already do this and it’s a fantastic system for L2’s and other networks trying to get rid of third-party bridge risks[5]. Any system (like Eigenlayer) that could allow for experimentation with enshrined oracles or bridges, without a hard fork, is awesome and worth a look.

<b>Obstacles to success (gotta keep it positive)</b>

*(In no particular order)

    * overstated crypto-economic guarantees.
    * it doesn’t make starting a trust network any easier.
    * restaking strips the token startups of crucial value capture/ business model.
    * stETH and LST’s are custodial cesspools.
    * value is unlimited.
    * overstated crypto-economic guarantees.

Imagine you’re a 22-year-old degenerate and you need a new pad because your stepdad’s a dick and doesn’t realize it’s 20 fucking 18 and shits changed. Naturally you move to the nearest city and get a 1br place near some bar where you met the girl of your dreams last year. As is always the case, the landlord makes you put $1000 down as a security deposit. This is for a few reasons, namely that a) it shows you’ll likely be able to pay rent at the end of the month and b) because if you trash the place, he at least has some money to pay for a cleaner without having to take you to court. After you make the deposit, the landlord is a hippy and gives you a receipt for the deposit. For the sake of the example, he says he doesn’t want to know who you are, but if you (or anyone) give him this receipt after you move out, he’ll give them $1000.

Now imagine you need a rental car. They also want a security deposit of $1000 (steep, but rentals are absurd in our imaginary universe). Would it in any way make sense for the car dealer to take that $1000 receipt?

The answer is probably not.

The obvious issue is that if you give it to the rental company and then trash the apartment, that note is worthless.

Sure, maybe the car dealer doesn’t actually want that $1000. Maybe it’s just a reputational thing and he wants you to prove that you’re an upstanding young man with an apartment and enough money for one. In that sense, this works great. But that’s reputational; it’s not crypto economic. You could never say that the rental company has $1000 worth of security.

And this is the problem with restaking. You don’t actually garner more security. It’s solely reputation based.

For any system, you should attack the system if:

        profit from attack > cost of attack

Restaking doesn’t change the cost, it just increases the ways in which one can profit from an attack on the system(s). Not only can you throw the underlying validation, you can also throw the restaking protocol’s services. In our examples, now you can trash the rental and the apartment and only lose $1000! So if you get $600 worth of joy writing graffiti in the apartment and $600 worth of joy smoking and doing donuts in your rental, the once safe system is now unsafe because you only used $1000 to cover what was once $2000.

<i>It doesn’t make starting a trust network any easier.</i>

The main mantra is “use ETH’s trust network”. But you don’t have ETH’s trust network. You have an opt in subset of that trust network. Yes, I agree that having a marketplace for people to go and look for opportunities is nice, but you still have to sell people on the idea of validating your thing, and let’s be honest, most smaller startups won’t be able to sell Lido or a big exchange on validating their system. The juice won’t be worth the squeeze.

A big problem for Eigenlayer (and most established tokens) is that in the age of defi and hyper-liquidity, validators can already loan their stETH, get some other token, and go do something else.

Imagine a protocol that doesn’t use Eigenlayer. They start their own token that you have to buy and stake in order to validate. If you have stETH, you can sell it (or lock it for stables) which you can then buy that token with and start validating. There’s nothing stopping you from doing this now, the only difference is that this system works way better because now the value is in the protocol’s token, not some potentially worthless LST with centralization / complexity risks.

Using restaking primarily benefits the big guys or those validators that make the LST’s. It gives more demand for their tokens and makes them more profitable in exchange for their reputation.

For those small guys (say the dude on discord who doesn’t have stETH), now instead of being able to buy a relatively worthless token at the beginning, he has to buy stETH to lock up, a likely bigger capital requirement.

<i>Restaking strips the token startups of crucial value capture/ business model</i>[6]

By saying you want to just use stETH and not use a token is similar to old arguments from pre-2019 where people thought everything could be or be on bitcoin. Technically yes, but practically not really.

As someone who runs an oracle[7], I can tell you that getting rid of the token would not really help you in your quest for usage or security. One of the main selling points of tokens is to bootstrap something which doesn’t have network effects or a business model yet. By stripping away your token and using base ETH instead, you get rid of the bootstrapping effect because you remove the ability of the protocol to print inflationary rewards in exchange for security / activity.

Back to imagining, if you’re going to start an oracle with a new token, it’s exciting. You can say you’ll print tokens for staking and have 10% inflation for those pushing data. It’s awesome. Early degens come in and start reporting, showing liveness for users, and working out the kinks. It also pays well for those early guys if the protocol ends up doing well.

Now if you use eEgenlayer, the utility of the token (staking) is gone. Maybe you can still do a worthless governance token, but please spare us. The bigger issue is that you’ll need to provide an actual return to get people to start validating your network. They won’t just have to stake illiquid altcoins with purely speculative value; now they have to stake stETH, something you can already go get a decent return with.

This means that your protocol will need to match, and likely exceed due to nascency risk, the current rate for lending stETH. If you want to show liveness, you need to pay real cash money. You need to pay before you have any users, and you’ll need your users to pay right away. This is a nightmare for startups that didn’t raise boatloads of cash. It’s sort of a dirty secret out there that all infrastructure (oracles, bridges, etc.) is basically free for users because retail token speculation pays for it[8]. Oracles that try to get people to pay have an insane uphill battle and decentralized bridges that need to pay more than just gas costs for a multisig are at a huge disadvantage.

So my advice to upcoming infra projects… lean into the token. You’ll need it and hopefully it can give you a shot if you’re lucky. Customers NEVER turn you down because you don’t have the security, it’s almost always because the other guy’s free and much faster due to faux decentralization.

<b>stETH and LST’s are custodial cesspools.</b>

I’ll just say it, liquid staking is a disaster for a decentralized chain. Fungibility issues lead to centralization. The distribution reality of centralized exchanges further exacerbates the problem. And finally, the custodial nature makes the entire underlying chain unsafe in the exact same ways CEX’s that stake in general do.

Any system that adds rewards for LST’s further promotes their existence and reduces the reward given to individual stakers.

We live in a global, liquid, and easily convertible world. All value can seamlessly be transferred into other value. If a normal staker gets 4% on their stake, but Eigenlayer offers an additional 2% (say risk adjusted for those econ folks), the equilibrium is not that all stakers will get 6%. Assuming the eigen rate is inflexible, the end outcome is that more people will stake in the system, driving the reward for ETH stakers down to 2%. Interest rates in general aren’t set by Ethereum and as long as value can flow freely to yield, you don’t just have an infinite money machine for stakers. We know this lesson from the last 20 years. More money will flow into the system looking for yields and it will drive rates down to a global equilibrium. Rates are not set by crypto and we can’t escape this.

<b>final counterpoint — value is unlimited</b>

The idea that we need to use an existing value source to secure something is backwards. The argument that we need validators from some trusted group, using an asset with known value, is absurd. I love Ethereum and its permissionless validator set is probably the best of any network; but enshrining their position and the value of ETH is not the solution.

One of the coolest parts of crypto is that we’ve literally created trillions of dollars’ worth of value out of thin air. We’ve taken a simple PoW scheme and expanded it to the thousands of monetary experiments going on today. Inflation, governance, privacy, finance; crypto is touching, researching, and launching products in every aspect. The diehard maxis who pushed the theories of merge mining, “build on bitcoin”, “all alts are shitcoins”, these ignore the fact that crypto’s scaled not from solving “scaling” in the tech sense, but by cloning and morphing into the vibrant ecosystem we have today.

Let’s not limit builders by pushing them to use existing networks. Pushing systems of old value (e.g. gold, the US dollar, BTC, …now ETH), with known distribution and power centers…. this isn’t the dream. Dreams of equitable wealth distribution, markets that actually work, opt-in systems that bank the unbanked and promote innovation, this is going to come from new trust systems. So don’t tell projects to lock up old value and trust this group of people. Tell them to do the hard thing and make something new, tell them to make the new value and reap its rewards.

<b>Final Thoughts</b>

Eigenlayer is a neat idea. Fits nicely with merged mining[9], rehypothecation, and all other disguised or over-engineered forms of leverage for existing capital. On a positive note, I think ideally it can be used as a good step for signaling that the validators support a certain upgrade (e.g. do we all want to run a native bridge… if yes, let’s signal it here and get some customers started). You could also make the argument that it’s net positive for ETH the token because it will likely force more people to buy ETH to run validators, but once again, whether this adds any security or usage to Ethereum is up for debate (doubtful in my opinion[10]).

Overall trust networks and markets in general are hard to bootstrap, and even harder to get or keep decentralized. I think the better solution to bootstrap systems by native validators would be to tie MEV into your system in some way so that the validators sit in a trusted position to extract rewards. Can’t wait to see the experiment launch though, and I’ll probably even try it out myself. Fingers crossed they just don’t launch with admin keys and upgradeability….[11]

<p align="center">
    <img src= './pictures/sreeram.png' width="800" />
</p>

<b>Footnotes</b>

[1] **Last minute addition: Vitalik just wrote an article on how EigenLayer (or any consensus mechanism piggy backing off of ETH validators) is bad for Ethereum as a whole. Note that this article doesn’t really go into that. I mainly talk about why it doesn’t work as well at doing what it says it does, not necessarily it’s negative effects on Ethereum. I won’t attempt to re-explain either; super easy read and highly recommend: https://vitalik.ca/general/2023/05/21/dont_overload.html

[2] https://www.coindesk.com/business/2023/03/28/staking-protocol-eigenlayer-raises-50m-amid-crypto-winter/

[3] https://github.com/Layr-Labs/eigenlayer-contracts

https://github.com/Layr-Labs/eigenlayer-contracts/blob/master/docs/EigenLayer-tech-spec.md

https://www.eigenlayer.xyz/

[4] https://ethresear.ch/t/enshrined-eth2-price-feeds/7391

[5] You already trust your validators, so best bridge ever. Low-key prediction is that all chains will natively run bridges to Ethereum and that will be the one trusted way to get everywhere (just through Ethereum)

[6]On a side note, this reminds me of dollarization; or the idea that countries (mainly in central and south America) should forego their own currencies and use the dollar. It was a disaster and removes the independence and flexibility of the country. But that’s for another article.

[7]www.tellor.io

[8] Cough, cough LINK

[9] https://sec.cs.univie.ac.at/fileadmin/user_upload/i_sec/docs/teaching/thesis/azamyatin_merged_mining.pdf

[10] And vitaliks fwiw

[11] They totally are…. https://github.com/Layr-Labs/eigenlayer-contracts/blob/master/src/contracts/permissions/Pausable.sol sigh
