<h1>Oracles x AI</h1>

What are the AI opportunities for Tellor? 

We’ve been asked this and other questions many times.  How does Tellor utilize AI? How does AI fit into the broader narrative of determining truth? How does AI replace the need for oracles? 

The truth is we’ve been looking at it.  As someone who’s been through the cycles a few times, it’s ok to take a little time following some of these trends.  It’s still not completely clear whether AI is even something a project would want to put into their narrative or just another passing phase like NFT’s, memecoins, or hamster racing. There’s immense promise to AI, but at times can seem like a hammer in search of a nail; a sentiment far too familiar to those of us in the broader web3 space.  

So for the sake of transparency and to open up the discussion to a wider group than my inner circle, I’m laying out the various options and pieces of consideration that an oracle may have as it relates to AI.  I’m going to split the article into three phases; AI as a tool, a customer, and a narrative.  Each has completely different answers that may relate to each other, but the split will allow us and the broader crypto space to address each piece as a separate conversation since zero, one or all could be potential paths forward. Whether or not AI will be relevant, answers to questions regarding its existence are necessary to be engaged with the current narrative and we at Tellor should have an opinion. 

<b>AI as a tool</b>

Even though AI can be a powerhouse of a technology, it doesn’t mean it’s the right fit for an oracle.  We all know that an AI agent can scrape the web, answer api calls, and put them into smart contracts.  The real questions would be more along the lines of:
Where does decentralization come in?  (is this competing or complementing?)
Does a blockchain or crypto-economic security make sense here?
Does it do these things better than human-verified systems?   

We might finally be past the stage of needing to shoehorn decentralization into a narrative, but as this article is about AI’s relevance to oracles, we should recognize that most oracles as they stand are glorified middleware with some questionable level of decentralization.  So without pontificating about future oracle demand and how it will change, the most obvious and easy way for an oracle to get involved with AI is by simply using it as a tool.  There are however two levels of utilization that come from AI:
the backend UX or
the AI itself as a fundamental player in the oracle architecture  

For example, if a current oracle forked their reporting software and instead of hardcoding API’s asked an LLM to grab spot prices from top exchanges, this would be completely allowed and easily integrated into almost every system.  We might not even know they’re doing this or using AI and we wouldn’t need to change any underlying oracle code (the smart contracts or chain) at all.  This would be purely a UX improvement (assuming it worked), as it makes adding new data points much simpler (you don’t need to find and program API connections).  On the contrary, if we add AI reporters as a separate class of data reporter (as opposed to the current human based bot), this might fundamentally change how we want to distribute rewards or how we handle determinism and disputes. 

<b>AI for UX</b>

<u>Potential Usecases:</u>

  - AI as a tool for web scraping and data collection
  - AI as a reporter for queries
  -  AI as a tool for integrations (e.g. writing smart contract plug-ins)
  - AI agents as monitors for updating data
  - AI for data source selection
  - AI for marketing and social media

For all these AI UX improvements, they can be done relatively quickly and in a completely opt-in fashion for reporters and users. The big issue with any of these upgrades is just in the accuracy, dependency, and scope we place on the AI.  As an example, if we use AI in the gathering of price data, there’s a big difference between asking it to “get the price of TRB” vs “go to these 4 exchange websites, scrape this specific price point and aggregate them using a median”.  The former might require clean up after the fact but could allow for faster data additions, while the latter will be more similar to traditional models and still take significant developer time to find and vet sources.  It’s still an unanswered question whether you tell the AI the proper sources, give it qualifications of proper sources (e.g. the highest volume exchanges), or simply give it freedom.  Ideally testing would be done on all of the above to see how much freedom you can give it and how it affects accuracy.  I fully expect all oracle companies are already experimenting with these improvements, it’s just a matter of whether or not they’ll actually push it to production (or let us know).

<b>Fundamental changes for AI</b>

<u>Potential Alterations:</u>

  - Agents as a separate reporter class
  - Bounties for top AI models w/ regard to predictions (e.g. mini prediction markets for rewards to get the best models for certain ID’s)

For more fundamental changes to a system regarding AI, we could make AI agents a separate reporter class, with validators enshrining, or reporters running, different AI agents and reporting the results.  By giving full control of the data sources to the AI, it can greatly increase our ability to do new queries (it does basically everything), however the chain will need new methods for verification as data quality becomes harder to measure .

Another option would be to look at our system as a bounty program for the best AI’s. If we embrace the different models, we could do rewards such that AI models post the answer instantly, but then rewards are given to the “most correct” as determined by human reporters (maybe via a manual dispute process).  This would in effect serve as a contest for generic AI models to produce the best answers, something which might be a neat byproduct that would allow crypto to maybe even help the AI field. 

<u>Some of the open questions / issues include:</u>

  - How do you know a validator or reporter running the actual AI software?  
  - TEE’s have been proposed as a solution, but this is a can of worms to say the least.
  - What models do you have the parties run? 
  - If you let parties choose, there’s an incentive to just pick cheap ones
  - How much data do you push on-chain?
  - This is always a problem for oracles, but limiting AI to specific one point answers might limit the addition of context to qualify an AI’s answer.   
  - Do you have slashing or softer penalties? 
  - If redesigning a system, you have problems if parties are not incentivized to run newer/better models, but they won’t if they’re worried about being slashed.  They will want to run the same as everyone else. 
  - The inefficiency of decentralization 
  - If AI is already expensive, now let’s split it up and have 100 people run the same exact thing…. see the problem?  Even if we all run the same code, if we don’t use TEE’s, is it even deterministic to slash or penalize on? 
  - What are the dependency issues?  
  - If AI models turn into a 1 or 2 companies win kind of game (which it probably will), you could be very centralized by design. If you assume the crypto space wins and all finance/smart contracts are powered by AI oracles, are we just handing total control over to those who write the AI?

<b>AI as a customer</b>

How does an AI know facts? It can scrape the web and ask, but in the world of misinformation, how can the AI tell the difference between fact and fiction.  There’s a consistent race between a) creating tools to parse large amounts of data for the truth and b) tools that create even larger amounts of data to fool a.  Crypto can help solve this by having stake and reputation linked to statements to allow for greater confidence in the accuracy of certain sentiments. 

This exact problem is something we’ve had potential customers already reach out to us about (a nice sign about PMF, but beside the point).  If an AI agent has a customer that gives it information on some news story or claim(e.g. our XYZ coin has partnered with Google); how do they verify it?  As of now, they can scrape the web, but this is subject to manipulation and the answer may not even be available (e.g. is there a paywall on the news source?).  

Once again, as with using AI as a tool, there are two potential paths for an oracle.  Do you want to restructure the system to fit better for AI as a customer or do you want to just enable AI agents to query the current oracle.  Both are fine, but one predicts a world more consumed by AI than the other. 

<i>current generic oracles for AI</i>

We can just enable AI to use tellor.  Writing tools and integrations into agent kits could allow the agent to ask string queries and/or other data requests that reporters could answer.  This would work out of the box and could happen now with tellor or any other oracle that allows generic questions (or more narrowly for specific ones). 

<i>a real-time oracle for AI via prediction markets</i>

Another option would be to just create a new oracle to answer real time questions for AI.  The potential here would need some restructuring from current designs.  You would post questions and then have parties(people or another AI) answer it (potentially long answers).  Then anyone can place weight behind the outcomes (e.g. all the reporters put stake behind certain opinions or make their own if the option is not available).  Then if you did a decision market (example hourly for automatic or daily for human based), you could then give rewards to the participants and even winners in the case there is no dispute.  

<i>oracles as a notary and standard for truth</i>

This seems to be the current direction of most oracles.  They post some high quality, well defined data for consumption(e.g. you post a price feed, the cpi, reference bitcoin price, bridge result, etc. and you let anyone grab the signed data). There are still open questions on the necessity of decentralization vs transparency in this design, however this could be useful in the AI context as well.

By serving as a decentralized notary, it would be up to those looking to interact with the AI to verify information first.  They could have an oracle report or sign off on some fact that can then be made available to an agent.  It’s a more async, or slightly slower, model than on-demand requests, but oracles would need to redesign their output to offer support as a trustworthy benchmark with facts and context. By acting as a “pre-check” for AI systems, parties could be required to “register” facts as they would fill out an application form and then get them signed off on by an oracle before the AI interaction (e.g. if you want to have the AI admissions agent accept you to grad school, you need to upload your transcript to an oracle).  An oracle could potentially leverage zkTLS for this and begin to provide this service relatively quickly. 

Some of the open questions/issues on all three options:

  - What questions does the AI ask? 
  - Does it ask it in a format that oracles can provide a satisfactory answer for?
  - Can we programmatically answer the question?  
  - Do we have humans just waiting in the wing? 
  - Do we have AI answer AI questions and what security/loop issues does this create?
  - What answers do we give? 
  - We can potentially give very long, nuanced answers to the AI (i.e. fact checking is often very nuanced and being able to give context could actually help the LLM more than just giving an answer based on assumed meanings or intent of the question)
  - How is the time delay handled?
  - If we’re asking humans and not bots, how will AI customers feel about a delay?  

<b>AI as a narrative</b>

Is AI something we want to tie ourselves to?

The last decision any oracle needs to make is on branding, and this may or may not have anything to do with the decisions we make regarding the technology.  Rebranding as a “collective intelligence” or a “decentralized stack for AI” could be done with little or no change to the current structures.  The real question one would need to answer is what level of credence do we want to give the term AI or any related terms.  In the same way it would have been disastrous to pivot to serving the NFT craze of two years ago, is AI a fleeting trend if it becomes part of your narrative?

The oracle sector is a strong one.  There’s some big teams with well known names and brands that have earned respect.  At the same time, the oracle problem has completely changed over the past few years.  Few new users care if an admin is putting the value on-chain.  The current problem is just what API’s and whether there is actual liquidity on the sources.  It’s clear to see that centralized API aggregators are essentially the new “oracle“ (redstone, stork, pyth).  In a similar sense, I see little saving grace in tying a new company to price feeds as it’s a race to the bottom for cost and even more so, the idea of “startup” defi coming back with thousands of new customers is also dead in my opinion.  Defi is tradfi now.  We’re legal and it's bigger in the sense that traditional startup vibes won’t work and you won’t see the same volume of projects again.  A more professional approach to data quality, risk metrics, and a narrative around security will be important.  Additionally, you will need to have a narrative as to why any new methodology is better.  The old dogmatic rants of just being decentralized have sadly been moved on from. 


<b>AI as the “only” reporter -- the full AI pivot for oracles and data</b>

To predict the future, AI will be the oracle for low value projects.  

There will be someone that comes along and says, our AI is your oracle, our AI will find the data sources, and our AI will do everything.  It will just be an LLM running on a centralized server.  

For specific examples like price feeds and an inflation number, we can predict that AI will scrape the web, aggregate the prices, scrape social media for preferences on what to include in an index, and give a solid number. This is coming.  Being first to market might work, but the obvious question arises on how to establish a moat if eventually anyone will be able to ask any generic LLM to do this.  

The question for oracles now is whether AI is just not ready to automate the current products or whether there is something inherently wrong with AI systems that won’t work and/or whether a decentralized / crypto economic system adds something to it.  Additionally, we should pinpoint whether our system is valuable because of crypto-economic security or because we’re incentivizing humans or a community.  There are different outcomes for both, namely whether you want lots of centralized stake (e.g. BTC or Eigenlayer) or whether you’d rather have thousands of people (more community notes/ wikipedia style).

<b>Conclusion</b>

The oracle space, the blockchain space, and the entire tech space is changing rapidly. Where oracles fit in will be fascinating to see.  Hopefully this article will serve as a discussion for how any of us in the broader crypto ecosystem can start to provide value in this new paradigm.  If you have any questions or comments, don’t hesitate to reach out, www.x.com/themandalore9 
