---
layout: post
title:  "Celo Discord Validator Digest #2"
date:   2020-05-04 16:07:19
categories: [Celo]
comments: true
---
One of the troubles we have faced as a validator for [Celo](https://celo.org/) is keeping up with all the information that comes up in the Celo's [Discord](https://discord.gg/6yWMkgM) discussions. This is especially true for smaller validators whose portfolios include several networks. To help everyone stay in touch with what is going on the Celo validator scene and contribute to the validator and broader Celo community, we have decided to publish a **Celo Discord Validator Digest**. Here are the notes for the week of 27 April - 3 May 2020.

<!--more-->

## Discussions

### Threshold signatures:

Currently, if you validator goes down, you can replace it with another one by doing [key rotation](https://docs.celo.org/validator-guide/node-upgrades#upgrading-a-validating-node). However, the new validator will start signing blocks only after the epoch change, which, if the new epoch is far enough, will damage your uptime score and could even lead to slashing for downtime. Another option is to copy your validator signer key to another validator node. This could possibly reduce your downtime to the minimum, but not perfect from the security standpoint. One of the good solutions that is currently being discussed is the use of threshold signatures:

> **[@asa / cLabs](https://discordapp.com/channels/600834479145353243/601046166620078100/704043584651001897)**: My personal favorite solution for this is a BLS threshold signature based approach, similar to what polychain labs does, though I suppose it's not exactly what you're referring to https://blog.polychainlabs.com/tendermint/2020/03/26/threshold-validator-for-tendermint.html

Earlier Asa had already explained how those actually work:

> **[@asa / cLabs](https://discordapp.com/channels/600834479145353243/601046166620078100/698530834902155324)**: ... One future option here is to leverage threshold signatures. You could imagine running e.g. 3 validator machines in a 2/3 threshold scheme such that any one of your validator machines can go down without affecting liveness.

### Election thresholds for new validators:

After the Celo Foundation cast their votes, it became evident that those validator groups that didn't get to the top 50 of the Great Celo Stake-Off would find it hard to get elected because of the election threshold, e. g. the number of votes required to be elected as one of the validators: 1/1000 of the total current votes, which at the time of the discussion was already over 70k.

Many raised a concern that this would prevent new validators from ever joining the set and would lead to concentration of power among those elected.

**[@asa / cLabs](https://discordapp.com/channels/600834479145353243/697229909545713775/704329558727589979)** noted that this was intentional to avoid the situation when a validator spot becomes to "cheap" creating room for manipulation:

> As I've probably mentioned before, much of the proof-of-stake system is designed so that as many votes as possible are needed to get elected, making the cost of buying validator seats as high as possible for an attacker. This is the motivation behind the electability threshold – if there aren't 100 or more registered validators, you don't want to necessarily elect all validators, as that may make electing a validator very cheap. Without the electability threshold, the cost of electing a validator right now would be just the cost of registration. Theoretically, you'd be able to elect a validator with 1 wei voting for you, which would not make for a very secure network!

Asa also **[stressed](https://discordapp.com/channels/600834479145353243/697229909545713775/704360325285281792)** that after more cGLD holders go online and cast their votes, the 1/1000 eligibility threshold might not be a problem because the number of votes required to get elected will far exceed that threshold.

In addition, **[zviad / wotrust.us](https://discordapp.com/channels/600834479145353243/697229909545713775/704360872553873649)** reminded that there was a **[limit on the number of votes a group may receive](https://docs.celo.org/celo-codebase/protocol/proof-of-stake/validator-elections#group-voting-caps)**, so eventually the validator set will be full and groups that didn't get elected upon the vote unfreeze will make it:

> ...because of how vote capacity works too, you cant just jam votes into single group, people have to spread their votes around and it will get to 100 elected validators most likely.

He also [**noted**](https://discordapp.com/channels/600834479145353243/697229909545713775/704308738265448489) that there was so much more cGLD in existence that hasn't been used for voting yet, that this should be a concern:

> ... There is still tons of gold not activated from release gold contracts. (>100 million), at least 60 million of those are already liquid and released too. So we should expect even more gold to be locked and voting in upcoming weeks/months.

Later during the week, we indeed saw that validator groups outside of the top 50 started receiving votes from other voters (probably cLab's employees as [this post](https://discordapp.com/channels/600834479145353243/601046166620078100/705899663500247041) suggest) and many of them made it to the set.

### Governance duration:

There was an interesting discussion about the current governance procedures, the point of having both the `upvote` and the `vote` stages and their durations. As the first one is used to screen the proposals and prevent spamming the network with them, it also might cause some confusion.

> [**@zviad / wotrust.us**](https://discordapp.com/channels/600834479145353243/704805825373274134/704860511325388842): Something to think about would be that: combining upvoting and voting times. I feel like if I am a person looking at a proposal and I need to decide if I want to "upvote" it , I can also at the same time decide what I want to vote for it too.
>
> Maybe that is not the case for everyone participating, but for me personally, if I have to look at a proposal, might as well make a decision on what to do, instead of first making a decision to upvote, and then making a separate decision to vote.
>
> An option to combat spam, could be in the clients, were proposals are sorted by "total votes", so proposals that have most total "yes/no/abstain" votes show up as most important, so instead of having an upvote concept to just use voting as a determination of how important the proposal is.

> [**@asa / cLabs**](https://discordapp.com/channels/600834479145353243/704805825373274134/704861497490145391): I would still love a way to "batch" proposals, so that e.g. voting happens every other week between Monday and Friday.

> [**@zviad / wotrust.us**](https://discordapp.com/channels/600834479145353243/704805825373274134/704861623604477975): If voting duration is a week, that will already be the case since you can avoid missing any proposals, even if you check just once a week.
>
> In my mind, ideal setup would be if voting duration was 2 weeks, and you were able to vote as soon as proposal is in place. so instead of waiting for it to go through stages, you can cast your votes at any time in a 2 week time period.
>
> This would give flexibility for each individual user to decide when they want to do their governance actions. (it can be once a week, or once every two weeks any day of the week).
>
> (of course this would be very large change in contract, but maybe parts of it can be applicable to simplify the setup and increase engagement. Like allowing people to vote even before proposal is dequeued or approved, so they lock in their votes if they know for sure what they want to do with the proposal).

> [**@victor / cLabs**](https://discordapp.com/channels/600834479145353243/704805825373274134/705815856940056688): Governance durations themselves are a governable parameter, and we'd love for everyone to have a discussion about what it should be in the future. Starting out, it seemed prudent to make it go a little faster because the community is smaller and more in communication, but maybe it needs to be adjusted sooner rather than later. Definitely worth starting to talk about.

### Validator Directory:

Not so much a discussion per se, but **[brian / stakevalley.com](https://discordapp.com/channels/600834479145353243/601046166620078100/705904085475524708)** suggested that it would be nice to have a way to somehow showcase validator's participation in the community beyond just validating:

> A validator directory would be good - I think Validator Explorer on the website would be a good spot to showcase links to different validator websites (perhaps it could just link to the claimed domain and/or some other metadata claim).
>
> It'd be interesting to capture community engagement somehow on the Explorer outside of the core validator metrics like uptime/etc. Things like accepted PRs to Celo repos, engagement in the Discord community, etc.

## Useful info

* If you want to update your validator group commission, here's a tip from **[victor / cLabs](https://discordapp.com/channels/600834479145353243/697229909545713775/704749551352938627)**:

  > If you want to update commission, you need to call `validatorgroup:commission` with `--queue`, then after the update delay (set to ~3 days), call with `--apply`... (Context: Update delay is a protection measure so groups can't attract members with generous reward shares then change it abruptly)

* We now have the [governance channel](https://discord.gg/zKCM2K) in Discord to discuss governance proposals and [account metadata channel](https://discord.gg/ZQzQmz) for all things related to registering metadata.

* Slashing penalty now kicks off if a validator has been down for ~8 hours and not 12 hours as was previously announced:

  > [**@victor / cLabs**](https://discordapp.com/channels/600834479145353243/697229909545713775/705461774723448862): Downtime slashing is currently was set to ~8 hours on RC1 after a review of the parameters between Baklava and RC1 launches.

* Multi-proxy support is in the works, but it might take a while until we see it implemented:

  > [**@victor / cLabs**](https://discordapp.com/channels/600834479145353243/601046166620078100/705522903810179102): We are currently working on it, and optimistically it will be ready in 4 weeks, but with the limited developer resources and priority of getting the network up and running for users, it may get delayed.

* [**hqueue / DSRV / CeloWhale.com**](https://discordapp.com/channels/600834479145353243/601046166620078100/705687942320095312) and [**syncnode (George Bunea)**](https://discordapp.com/channels/600834479145353243/601046166620078100/705688593842176000) reported suspected memory leak in geth. Keep your eyes peeled!

* Last week, many of us again [saw](https://discordapp.com/channels/600834479145353243/697229909545713775/705794154562584616) our validators unexpectedly missing block. Looks like it indeed had something to do with some genesis validators being down/slow because it seems that the situation has largely improved since elections were enabled. Meanwhile, **[zviad / wotrust.us](https://discordapp.com/channels/600834479145353243/697229909545713775/705806701109969018)** summarized why it was happening:

  > here is my understanding of what is going on: most likely case is that there are some genesis validators that are either slow or have some other sort of an issue (maybe they are down). That means the 1/3 of validators that are not in the main singing cohort when those genesis validators are proposing (or maybe when they are next in line to propose) never get their signatures sent out.
  >
  > Because only 2/3 of signatures are necessary, the delivery of rest of the 1/3 of signatures are more prone to failure or to be missing.
  >
  > Also because there are no elections, the proposing order of genesis validators is fixed and doesn't change epoch by epoch, so it is always the same set of 1/3 of validators that are hitting the issue (instead of the cohort of "unlucky validators" changing every epoch).

* **[peterldowns / cnstnt.xyz](https://discordapp.com/channels/600834479145353243/601046166620078100/705626006588751933)** shared a tip on how to connect your locally installed `celocli` to a fully synced remote node using ssh tunnel:

  > I've found that using an ssh tunnel works exactly as well as I thought it would. With a baklava accounts node set up as normal, running on a machine that I have an ssh config entry for called `c-accounts`, I am able to use a locally-installed `celocli` to interact with the celo network with the following ssh command:
  >
  > ```
  > ssh -f -N -L 8545:localhost:8545 c-accounts
  > ```
  >
  > This sets up a tunnel so port 8545 on the computer you run this command from is mapped to port 8545 on the c-accounts machine.
  >
  > ... makes it easy to keep an accounts node synced in the cloud and securely accessible from your administration laptop from anywhere in the world.

* **[syncnode (George Bunea)](https://discordapp.com/channels/600834479145353243/601046166620078100/706523958446653520)** started publishing snapshots of the chaindata with `--gcmode=archive` and without it which you can download here (change the date in the filename to get the latest one, e. g. `202005041500UTC` to get the snapshot published on 4 May):

  [http://syncnode.ro/celo/archive/chaindata_202005031500UTC_noarchive.tar.gz](http://syncnode.ro/celo/archive/chaindata_202005031500UTC_noarchive.tar.gz)

  [http://syncnode.ro/celo/archive/chaindata_202005031500UTC_gcmode=archive.tar.gz](http://syncnode.ro/celo/archive/chaindata_202005031500UTC_gcmode=archive.tar.gz)

  But keep in mind the following remarks from **[zviad / wotrust.us](https://discordapp.com/channels/600834479145353243/601046166620078100/706528474981990531)** that it might not always work as intended:

  > If you copy `noarchive` chaindata and start a new validator node, you have fair chance to get missing trie errors for quite a bit.  At least for a full epoch (and maybe more?). So something to be careful about if you bring up new emergency validator node using it, because it may not actually work. (I am not really sure why this is, maybe it needs data from another folder too? Maybe it is an accidental if node where data is copied from doesn't exit cleanly) -> if you copy `gcmode=archive` chaindata and start a node without `gcmode=archive` flag, old data will not be pruned by default. I think there are ways to force geth to manually prune the old data that was copied in `chaindata` folder, but it wont do it on its own. So if local disk space is a concern it is something to be aware of.

## Community

* **zviad / wotrust.us** created a [voting tool](https://www.npmjs.com/package/celovotes) so that validators who are no longer running a validator or a group in baklava could use it to continue to automatically deploy votes for other high scoring groups. He also created the [governance tool](https://www.npmjs.com/package/celogovernance) that gives more human readable output for governance proposals.
* Thanks to **[kp](https://discordapp.com/channels/600834479145353243/638489933740376068/704503463844773930)** you can now exchange Celo **Baklava** assets using your Ledger device at [https://celoist.com/](https://celoist.com/). Vote management support is coming soon.
<br>
<br>


-----------------------------------------------------
<br>

<center><strong><font size="+1">If you want to receive the digest directly to your inbox, you can subscribe to our Substack newsletter below.</font></strong></center>
<br>
{% raw %}
<center><iframe src="https://moonlime.substack.com/embed" width="480" height="320" style="border:1px solid #EEE; background:white;" frameborder="0" scrolling="no"></iframe></center>
{% endraw %}
