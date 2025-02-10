<h1>blue shell strategy — a path for removing centralization from the ETH validator set</h1>

In light of my post describing a new discouragement attack, I present here an optimal strategy of discouragement to reduce centralization in the validator set. This post will address the most common concerns of “who do we discourage” and “how do we keep it objective”. The short answer for both is that each individual validator should target the largest concentrated actor they see, regardless of size. The article will finish by going into some challenges and traps present in the journey to a desired game theoretic outcome.

<b>introduction</b>

To reiterate the goal, we’re designing a system with a globally decentralized and anonymous validator set that is not owned, held accountable, or censorable by any third party corporation or government. Additionally, the validation of the chain should be open to all, including parties using standard consumer grade hardware.

Currently the Ethereum validator set is threatening to be centralized by economic forces deriving from liquid staking tokens, restaking protocols, and traditional financial products (ETFs). If we do not protect the integrity and decentralization of the validator set, the cause will be lost.

To briefly go over the discouragement attack from the previous post, participating validators ignore attestations from targeted validators when they (the participating validators) are the committee aggregator. There is no penalty for this as they will normally not be chosen (the proposer picks the attestation list that has the most number of attestations), however the attack succeeds when participating validators are also the proposer, as they will choose the aggregated attestation that does not include targeted validators. This will cause the targeted validators to miss out on attestation rewards for that block and potentially expose them to inactivity leaks (slashing) depending on the size of the concentrated actor. Long story short, once you hit ~10% of validators in agreement with a specific group to discourage, you can reduce their rewards at the percentage of validators supporting (e.g. if 20% of validators participate, you can reduce the discouragement target’s rewards by 20%).

<b>the plan — a writhing criticism of an EIP should teach them a lesson</b>

As with any penalty in the system, any implementation must avoid this becoming a popularity contest amongst validators (each LST or validator group saying the other is worse). There should be no alignment police and we don’t want there to be.

For that reason an example EIP for this strategy is simply: “all parties are to discourage the largest concentrated group of validators’.

Then you leave it at that. The definition of largest concentrated group is of course subjective, but can mean anything from a CEX, to an LST, to a restaking protocol. It’s up to individual validators to grab the list of validator indices associated with what they perceive as the largest concentrated actor(CA). Even if there is not complete agreement over the set, the system will work to reduce CA rewards if there is any overlap in the lists. The hopeful outcome is that everyone participates and parties are most profitable as anonymous sets of solo stakers. The end goal is to reduce or eliminate usage of the validator set as a means for alternative systems (LST’s, restaking, financialized tradfi products).

As for largest concentrated actor selection, one option is to make the target list for each validator public. Knowing who is targeting what CA will allow for quick alignment on the issue and there will probably be researchers, oracles, and bounty contracts leading the way in identifying and programmatically updating the list.

Some may come back with a critique that we should only discourage concentrated validators if they cross some threshold; but this is more difficult. If all other validators discourage someone at 40%, the most rewards they can stop is 60% as they’ll still get attestation rewards from their own blocks. On the other hand, if you can stop a CA when they’re at 5%, it makes a shift in business plans necessary. Identifying threshold violators is also tricky. If the threshold is 20% and two doxxed parties are at 15% and their governance token ownership overlaps…are they over the limit? This could be tough to analyze. Under the blue shell proposal however, if 15% is the largest group, they’ll be discouraged and economically encouraged to divest.

<b>the desired outcome — self inflicted antitrust laws</b>

What if a staking provider does manage to get large while evading detection?In order for this to happen, this hypothetical large provider must have:

    * Carefully distributed its validators geographically
    * Carefully distributed its validators in different IP subnets, including likely residential IP regions
    * Carefully avoid registering any real-world legal entity that could be investigated and/or prosecuted
    * Carefully chose a diverse set of operators each with near-perfect opsec
… And if all of that happens, well: [Mission. Fucking. Accomplished.](https://xkcd.com/810/) Ethereum is now very resiliently decentralized.

The truth is that we want people to be afraid of being known. Bring the dark forest to validator sets. Any LST will be forced to go through centralized entities that might as well be investing them in treasuries, but even worse are subject to a whistleblower in their organization doxing their validator indices and ruining the whole thing. Any restaking operation would never work because the validators would be known and targeted. No one would leverage the validator set and this is the point.

Over time you’d have smaller validators run a few clusters here and there, but if you beat them down to everyone being a single validator or close to it, no one would even attempt a publicly coordinated effort without writing off their rewards.

<b>trap and challenge scenarios</b>

<i>retaliation scenario</i> — Starting this change is the most difficult part. We have very large players in the validator set now and if broad support is not reached, one potential blowback scenario would be that the CA retaliates and discourages anyone participating in the discouragement attack. They would probably pitch it as themselves protecting consensus integrity and they would discourage anyone they detect as participating. This could be dangerous because the CA could initially be larger (i.e. reduce more rewards) than the participating validators. Overall, they might not do this if they viewed the press around doing such an action as a negative, but if the CA threatens to do this, it could severely hamper participation in the discouragement of the CA. For this reason, we’d hope that an EIP or other “upgrade” initiative would be enough to kick start support over this threshold.

<i>cartel scenario</i> — Here, you have a majority group agree to discourage anyone not in the majority groups. The example would be something like 8 different LST providers all agreeing to split the market (stay under a threshold), but then would attack anyone not in their cartel (e.g. vampire LST’s, CEX’s starting to dominate, or just other non-identified validators). This is a real risk in the current market because LST’s and restaking protocols have billions of dollars in governance tokens riding on them staying active. To break any cartel behavior, social slashing and/or censorship at the app level may be necessary (e.g. don’t include their token transactions).

<i>aligned cartels</i> — We already see it, but this will likely grow to nauseating levels with this proposal. You will see all LST’s / restaking / governance tokens SAY they are aligned and that they are really the best thing for the protocol. They will act as though this upgrade is not meant to target them and they are actually groups of solo staker specifically designed for maximum decentralization and Ethereum alignment. But this is not the case. This strategy is 100% meant to include them. If you can tie the validators together in any way you should count it as a single entity(an LST, all run by a CEX, all in a restaking protocol, all run from the same IP address, a co-op of solo stakers, etc.). It’s up to each validator to pick the grouping, but the standard should be to force coordination out in every way possible. Tell everyone to stay away from using the validator set for anything but validation.

<b>external rewards — the pit of restaking</b>

If you add in external rewards, a big problem could occur. What happens if validators actually don’t care about base rewards? What happens if concentrated actors make enough off of MEV and restaking that the attestation and sync committee rewards are meaningless to them?

To beat this, you may have to start ignoring CA blocks (assuming you have >66% participating validators). This is dangerous as you would need more coordination on the target list, but would work if it was unanimous for certain parties. MEV rewards for the CA would go away and coupled with the inactivity leak of enough participation, the penalties would be quite severe to the CA. Overall, more research will be needed in this area if this discouragement is not enough to dissuade the economics causing centralization, however I’m hopeful that just throwing out these ideas would be enough to move serious players from having threatening levels of control.

<b>enshrinement of the idea</b>

The main downfall to this proposal is that you’re throwing away valid attestations. Since many concentrated actors could be 10, 20, or more percent of the validator set, this would represent throwing out a lot of attestations and quickly inactivity leaking participants who are of this size. Of course we would hope that before this implementation ever took place, the centralization would be addressed, but the initial state should be handled for. One in-protocol change we could make is to allow the attestation to count toward the threshold, but still penalize them in some way (e.g. remove attestation rewards, but no inactivity leak; or something similar). This option would make it much less disruptive on the chain and could minimize unforeseen consequences if the CA target is too large.

<b>conclusion</b>

This article should be a great starting place for continuing discussions with stakeholders and developers in the Ethereum ecosystem as to the best path forward. With talks of reduced ETH issuance/ staking targets, we must recognize that the threats from concentrated actors are too large to ignore and must be handled before we can seriously discuss an equilibrium or even the economics of staking without external influences.

<p align="center">
    <img src= './pictures/blueshell.png' width="600" />
</p>
