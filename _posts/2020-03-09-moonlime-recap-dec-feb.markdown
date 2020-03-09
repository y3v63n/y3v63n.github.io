---
layout: post
title: "Moon Lime Recap: December 2019 - February 2020"
date: "2020-03-09 14:13:11 +0100"
---
Good news! We are not dead! In fact, we are live and kicking well. Check out our latest update to learn what we've been up to in the last 3 months.

<!--more-->

The end of 2019 and the start of 2020 turned out pretty busy for our small team so that we didn't even have time to publish any updates. Now that there is a small window when we can take a quick break, it is time to share all the exciting projects that we've been busy with.

First of all, after the numerous grueling testnets of 2019 we thought that it would be a good idea to take our time and concentrate on a handful of projects that we truly believe in. Thus we put all our effort and time into helping just a couple of new networks that we think will have impact and traction in the real, non-crypto world.    

<center><img title="Celo" alt="Celo" src="/img/Celo Logo Color.png" width="350"></center>  

[Celo](celo.org) has built a financial platform that seeks to empower any person in any part of the world to become a participant of the global financial system. We love their approach based on inclusivity and community participation. Their platform also allows anyone to build various financial applications, "including easier cash transfer programs, peer-to-peer lending, collaborative small-scale insurance, and other digital assets and wallets".

In early December, Celo launched the [Great Celo Stake Off](https://forum.celo.org/t/the-great-celo-stake-off-the-details/136) competition for prospective Celo validators that consisted of three stages. First, we learnt the basics of the Celo blockchain and gained operational experience. Then, participants tested their attestation services, a crucial part of the Celo's ecosystem. Finally, we got a chance to check the operational security of our validator setups and participate in governance and hotfixing.

Man, that was such a ride. The first stage went smoothly, and we didn't experience any issues. However, soon after the second phase began, when point counts towards the leaderboard started, we got hit by the notorious ["preprepare bug"](https://github.com/celo-org/celo-blockchain/issues/808). This kicked us out of the top 50 for a while, and we really never managed to fully recover. Luckily our attestation service functioned well and earned us a 20-percent bonus after the 2nd stage ended.

The most difficult part of this journey was the security audit, when a third-party auditor was to check our validator, proxy, attestation and backup validator setups. We literally spent two weeks working day and night to ensure that our nodes (we had as many as 5 of them!) met the requirements. On the bright side, we managed to learn a lot about how to make our setups more secure and will certainly use this knowledge for our validators in other networks. Our hard work paid off in full, and we scored 94 points during our audit, thus earning ourselves the Master Validator title (and a badge that is coming soon).

The bonuses and excellent performance of our validator at the end of the competition helped us finish the Stake Off at the 28th place and earn 20,000 Celo Gold (Celo's network token) that we are planning to use to launch our validator when the mainnet starts, which hopefully happens quite soon.


<br>
<center><img title="Regen Network" alt="Regen Network" src="/img/long_black.png" width="350"></center>  

We've been supporting [Regen Network's](https://www.regen.network/) testnets since last August.

In January, we took part in another Regen's tetsnet named Algradigon-1 in the course of which the participants tested Regen's network upgrade module [cosmosd](https://github.com/regen-network/cosmosd). During the two-week period we performed four upgrades all of which were executed with the help of the module, with one of the them taking the record 91 seconds to perform.

Being well-familiar with the network, we finished this testnet at the [8th position](https://docs.google.com/spreadsheets/d/1e0gty1O4zrCdqSQuZCsaq9zrDyfTXXbvcthza0EFOmc/edit#gid=0) scoring 899.32 out of 900 points. The next test network is scheduled to launch on 9 March, and we are certainly going to show our validator skills there too.
<br>
<br>

<center><img title="Centrifuge" alt="Centrifuge" src="/img/centrifuge.svg" width="250"></center>  

[Centrifuge](https://centrifuge.io/) invited us to join its validator program in mid-January, and we happily agreed. To put it simply, Centrifuge has built a solution that solves the problem of unpaid invoices in the B2B sector. It is quite common that in the business world invoices are paid in 30, 60 and even 90 days. Centrifuge allows businesses to tokenize such invoices and gain liquidity for them. This is done using Centrifuge's novel solution [Tinlake](https://medium.com/centrifuge/centrifuge-tinlake-adding-real-world-assets-to-mcd-68cbcb67e9a4).

Centrifuge uses the Substrate-based Centrifuge Chain to secure the Centrifuge Protocol and ["hold the shared truth of off-chain assets"](https://docs.google.com/document/d/1T4DF3XHs8l4gTzpnk6KASpD4JWjSoIWzxNX6DyVz__Q/edit).

We are currently running two validators on the [Flint](https://portal.chain.centrifuge.io/#?rpc=wss://fullnode.flint.centrifuge.io) and [Amber](https://portal.chain.centrifuge.io/#?rpc=wss://fullnode.amber.centrifuge.io) testnets and hope to be one of the genesis validators when the mainnet launches sometime in March.

We are really excited about the endless opportunities that Centrifuge opens for the DeFi space and its mainstream adoption and looking forward to be a part of this journey.

<center><img title="Edgeware" alt="Edgeware" src="/img/edgeware.png" width="200"></center>  

[Edgeware](https://edgewa.re/), a smart contract platform for the Polkadot ecosystem, has become known for pioneering the LockDrop, a mechanism for distributing tokens to those who locked their ETH for a certain period or signaled their intention to participate in the Edgeware network.

We've been running our Edgeware validator from the early stages of testnet and even were a part of the subsequently failed mainnet launch attempt in September. Following several months of fixing various issues, the network finally went live on 12 February.

After being a part of the validator set for two days, our [validator](https://commonwealth.im/edgeware/account/5Fgkcy5KGTCgvWPkoiaJURP4siSV5c3STfNc2JfGd1j2RaNh) was finally squeezed out by a number of large players who run multiple validators on the network.

We would like to get some support from the community and would welcome your nomination so that we could come back to the active set and join a handful of community validators who are trying hard to keep the network decentralized. Our validator's address:

    {% raw %}
    5Fgkcy5KGTCgvWPkoiaJURP4siSV5c3STfNc2JfGd1j2RaNh
    {% endraw %}



<br>
<br>

<center><img title="Kava" alt="Kava" src="/img/kava_logo_letter_256px.png" width="100"></center>  

Since the launch of [Kava Labs](https://www.kava.io/)' mainnet in November, our validator has been up and running with 99.99 percent uptime.

On 5 February, [we joined](https://testnet.kava.bigdipper.live/validator/1DD96BCD2E11BD6CF2D4156FB089242BEB5F9DB9) Kava's testnet-4000 from the genesis block. The team is using this test network to probe end-to-end CDP functionality that will soon be available on mainnet.

If you would like to support our mainnet validator, you can delegate your Kavas to our operator's address:

    {% raw %}
    kavavaloper1kc6vzheht92jwf0gtzhjk6jjht67rxhal9z04v
    {% endraw %}

Be sure to check out our [Delegation Guide](https://moonli.me/articles/2019-12/kava-delegation-guide) for detailed instructions.
<br>
<br>


-----------------------------------------------------
<br>

In addition to these networks, we are still working hard to join [Coda Protocol](https://codaprotocol.com/) at launch. We also joined Kusama's [100 Validator Programme](https://polkadot.network/join-kusamas-thousand-validators-programme/), NuCypher's [Come and Stake It (CASI) Incentivized Testnet](https://blog.nucypher.com/come-and-stake-it-incentivized-testnet/) and Oasis Protocol's [Quest](https://www.oasis-protocol.org/quest).

This is all for now. Share this post to support us, [follow us](https://twitter.com/moonli_me) to stay up to date and watch out for future updates!  
