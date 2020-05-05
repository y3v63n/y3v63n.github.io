---
layout: post
title:  "Celo Discord Validator Digest #1"
date:   2020-04-27 14:07:19
categories: [Celo]
comments: true
---
One of the troubles we have faced as a validator for [Celo](https://celo.org/) is keeping up with all the information that comes up in the Celo's [Discord](https://discord.gg/6yWMkgM) discussions. This is particularly true for smaller validators whose portfolios include several networks. To help everyone stay in the loop with what is going on the Celo validator scene and contribute to the validator and broader Celo community, we have decided to start the **Celo Discord Validator Digest**. Here are the notes for the period of 22-26 April.

<!--more-->

## Useful info

* If you want to use ledger and connect to a remote node to perform commands from it, the forno for RC1 is available at [https://rc1-forno.celo-testnet.org/](https://rc1-forno.celo-testnet.org/). The plan is to move it to [https://forno.celo.org](https://forno.celo.org) later.

* Celostats is available at [https://stats.celo.org/](https://stats.celo.org/). Unfortunately, many validators have complained that their validator names regularly disappear from the dashboard. It is usually fixed by restarting Docker container on your proxy (and sometimes on the validator machine too).

* Important note about rotating keys before rewards/transfer are activated:

> **[@asa / cLabs](https://discordapp.com/channels/600834479145353243/697229909545713775/703212256812335114)**: [I] suggest **not** doing key rotation yet. The RG contract will fund your **first** authorized signers with 1 cGLD for tx fees. If you key rotate, the second signer will not have any way to pay for tx fees until cGLD transfers are enabled.

​		Also, for those who locked entire amounts of cGLD on their RG account(s):

> **[@asa / cLabs](https://discordapp.com/channels/600834479145353243/697229909545713775/703212256812335114)**: ...[if] you locked up all your RG contract's cGLD, and the RG contract will always try to fund the first authorized signer address with 1 cGLD. The authorization fails b/c the RG contract has no cGLD to send the authorized signer. You'll need to unlock 2 cGLD, and withdraw it in 3 days, and then you will be able to proceed. Well really just 1 cGLD.

* If you want to lock accounts on your accounts node, you can perform the following commands to first list locked/unlocked accounts:

```
docker exec -it celo-accounts geth attach --exec 'personal.listWallets'
```

​		and then lock them:

```
docker exec -it celo-accounts geth attach --exec 'personal.lockAccount("<ACCOUNT_ADDRESS>")'
```

* If you have errors when executing `celocli` commands, prepend it with `DEBUG=*` so you can investigate errors further.

* In order to give a name to your group and validator, please refer to the following two commands:

```
celocli releasegold:set-account --contract $CELO_VALIDATOR_GROUP_RG_ADDRESS --property name --value <GROUP_NAME>
```

```
celocli releasegold:set-account --contract $CELO_VALIDATOR_RG_ADDRESS --property name --value <VALIDATOR_NAME>
```


## Errors

If you're getting one of these error messages, there's nothing to worry about:

```
WARN [04-20|10:23:51.062] Inconsistent subjects between PREPARE and proposaladdress=0xDcE0096C358E90c4645D68A53e897416e786D05F
func=verifyPrepare prepare_round=0 prepare_seq=216926 prepare_digest=0x67f7efdc143a6d937c6c9733d1caa38f2cf692806567600ee5d06e36236af578
cur_seq=216926 cur_epoch=13 cur_round=0  des_round=0  state=Preprepared address=0xDcE0096C358E90c4645D68A53e897416e786D05F
expected="{View: {Round: 0, Sequence: 216926}, Digest: 0x9eef35ea2de1d3c33c069674e80418e4295c611c39633d11e1950eddcc5df276}"
got="{View: {Round: 0, Sequence: 216926}, Digest: 0x67f7efdc143a6d937c6c9733d1caa38f2cf692806567600ee5d06e36236af578}"
```
> **[@asa / cLabs](https://discordapp.com/channels/600834479145353243/638489933740376068/701760565852504074):** [It just means] that someone sent you a `PREPARE` message for a different block than the block you're currently trying to validate.

```
INFO [04-22|11:16:05.005] Error sending all version certificates   func=Register
Peererr="write tcp 172.17.0.2:30303->54.39.176.72:58806: use of closed network connection"
```

> **[@trevor / cLabs](https://discordapp.com/channels/600834479145353243/697229909545713775/702479532153634857):** This is because the remote peer has closed the connection, likely because of the max peer enforcement on their side. This is expected but not the most graceful log message

```
INFO [04-22|11:16:08.793] Ethereum handshake failed                id=e1eea4fd60fe08f1 conn=dyndial err="Genesis mismatch -
 6f5dc2df52443f4125ccd298d922bfd4289a1746db748ef1f539847ce3575a55 (!= 19ea3339d3c8cda97235bc8293240d5b9dadcdfbb5d4b0b90ee731cac1bd11c3)"
```

> **[@trevor / cLabs](https://discordapp.com/channels/600834479145353243/697229909545713775/702479532153634857):** We found out that the genesis `6f5dc2df5...` happens when someone in the network forgot to init the genesis.

```
INFO [04-22|11:16:09.115] Error sending all version certificates   func=RegisterPeer    err="shutting down"
```

> **[@trevor / cLabs](https://discordapp.com/channels/600834479145353243/697229909545713775/702479532153634857):** Same reason as the other "Error sending all version certificates". Expected but ugly, this should be changed.

* If your are checking the status of your validator with `celocli validator:status --validator $CELO_VALIDATOR_RG_ADDRESS` and you see `false` in the `Frontrunner` field, don't freak out. This is because the election has not been activated yet. The output of the command actually say this: `Warning: Elections not available`.

* If your validator paints a picture similar to the one below, and your logs look fine, here are possible explanations of the issue:

  <center><img src="/img/Termius_44iBYnbgtu.png"></center>

> **[@asa / cLabs](https://discordapp.com/channels/600834479145353243/601046166620078100/702889132405293238):** Trying to collect **all** signatures is a bit of a feature on top which was added for uptime measurement, and is not necessary for block creation. Remember, your score is only impacted if you miss 12 blocks in a row, which doesn't seem to be close to happening. While we should absolutely diagnose and fix this issue I don't think it's any cause for alarm.

> **[@victor / cLabs](https://discordapp.com/channels/600834479145353243/601046166620078100/703708914721619988):** Based on the pattern, it's most likely that it has someone to do with a particular validator, and doesn't indicate anything wrong with your machine. We know 3 validators are currently offline, and that is likely the root cause, but we will know once we've investigated further. Because it is isolated blocks, it won't affect your uptime score.

> **[@Sami&Helga](https://discordapp.com/channels/600834479145353243/601046166620078100/702911034293485608):** Looks like blocks signed by `0x48CEDc58B10af13d688631bc3CB78a05b8A6E56a` have few signatures, there is probably some issue in their propagation.

> **[@syncnode (George Bunea):](https://discordapp.com/channels/600834479145353243/601046166620078100/703542025886105670)** My guess is that it only happens for genesis validator who re-use same signer key as the one from gist in  conjunction with the corresponding RG address.

* The notorious "preprepare" issue from the Great Celo Stake-Off is considered for closure: [https://github.com/celo-org/celo-blockchain/issues/808](https://github.com/celo-org/celo-blockchain/issues/808)

## Community

* [dsrv labs](https://www.dsrvlabs.com/) presented CeloWhale for the New Baklava at [https://baklava.celowhale.com/](https://baklava.celowhale.com/) . You can now add validators of your choice to the chart and choose mainnet or Baklava from button in top right corner. Soon, the mainnet version will be available at [https://celowhale.com/](https://celowhale.com/)

* [https://thecelo.com/](https://thecelo.com/) by [Bi23 Labs](https://bi23.com/) now supports the RC1 network. Also, you can add your logo to the list of validators and validator groups by getting in touch with <span style="color:blue">**Shen | Bi23 | thecelo.com#6675**</span> in Discord.

* [Pretoria Research Lab](https://cauldron.pretoria.tech/) has launched a faucet for Baklava at [https://cauldron.pretoria.tech/baklava-faucet](https://cauldron.pretoria.tech/baklava-faucet)

* If you missed the 24 April validator call, the audio recording is available [here](https://zoom.us/rec/play/6JUrcOj8pz43HNyV4gSDAfItW42_Ka2s0SMar6ILz0jkUHlXZFCvNeQVZ-WnKhpuEf4HgoSip3IS2sA5) and the notes [here](https://docs.google.com/document/d/1OrSnTjvYgHC41JxdwJ_fMrcQiJOanRaZLgZVqPscTBA/edit?usp=sharing).
<br>


-----------------------------------------------------
<br>

<center><strong><font size="+1">If you want to receive the digest directly to your inbox, you can subscribe to our Substack newsletter below.</font></strong></center>
<br>
{% raw %}
<center><iframe src="https://moonlime.substack.com/embed" width="480" height="320" style="border:1px solid #EEE; background:white;" frameborder="0" scrolling="no"></iframe></center>
{% endraw %}
