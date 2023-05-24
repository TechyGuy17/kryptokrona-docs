---
title: Frequently Asked Questions
---

# Frequently Asked Questions

### Kryptokrona node / xkrwallet Issues

**Q: I'm seeing an error in Kryptokrona `Proof of work too weak for block...` and the syncing stopped.**

This occurs because of the blockchain forking, generally when one mining pool has a very large hashrate.

This can be fixed by re-syncing the correct blockchain from scratch. See here.

**Q: I'm getting a "corrupted blockchain" error like this?**

```
2018-May-07 15:52:19.877323 INFO    initializing core
2018-May-07 15:52:19.908530 INFO    Importing blocks from blockchain storage
2018-May-07 15:52:19.908530 ERROR   Corrupted blockchain. Block with index 428973 and hash aafa7fd33d476535188bdd9e86ba51bb5e058be8e52367b78e9c0c03e74299c5 has previous block hash 2c0cf6c07612b9e1ea19c6922a56746b83cb42c7b11edfc4b185572225bb0f20, but parent has hash 26189359b64d4bb357a04b102a42a01d2771a3f3d80db3ca1b7395a2aeaede4a. Resynchronize your daemon please.
2018-May-07 15:52:19.924135 INFO    Closing DB.
```

Re-sync your daemon from scratch(see below question)

**Q: How can I re-sync the blockchain?**

Close any Kryptokrona-related software, then go to `%APPDATA%`, and delete the `Kryptokrona` folder.\
Reopen Kryptokronad/the GUI wallet and let it re-sync.

Alternatively, check [this guide](../guides/wallets/Using-Checkpoints/) for instructions on how to use checkpoints for a quicker sync, or try a [remote node](../guides/wallets/Using-Remote-Nodes/)

**Q: When I open Kryptokrona on a Mac, I get an error `Illegal instruction: 4`. How can I fix it?**

This is a known issue with older macs or un-updated macs.

Try entering this into a terminal -

```
curl -sL "https://raw.githubusercontent.com/Kryptokrona/Kryptokrona/master/multi_installer.sh" | bash
```

This automated script should compile the software itself, and place the binaries in ./src once done.

**Q: I've opened the wallet, and I'm getting lots of red messages like "It looks like Kryptokrona isn't open!"...**

```
It looks like Kryptokrona isn't open!

Ensure Kryptokronad is open and has finished initializing.
If it's still not working, try restarting Kryptokrona. The daemon sometimes gets
stuck.
Alternatively, perhaps Kryptokrona can't communicate with any peers.

The wallet can't function until it can communicate with the network.
```

You need to also open up `Kryptokrona.exe` and let it sync. Kryptokrona is your connection to the network, and needs to be open and synced whenever you want to use your wallet.

**Q: I've opened the wallet, and I'm getting lots of messages like "Your Kryptokrona isn't fully synced yet!"..**

```
Until you are fully synced, you won't be able to send transactions, and your balance may be missing or incorrect!
```

Your daemon hasn't finished syncing yet. Keep xkrwallet open, and wait until you are 0 days behind the current block, and for the daemon to print out a green message saying `Successfully synchronized with the Kryptokrona Network.`\
You can also type `status` in the daemon and press enter to see the current height it's at.

**Q: I think I should have more money in my balance than it is showing, what should I do?**

Re-sync your daemon from scratch(see [here](Frequently-Asked-Questions.md#q-how-can-i-re-sync-the-blockchain)) or use a [remote node](../guides/wallets/Using-Remote-Nodes.md)) if you're using the GUI wallet. If it still doesn't work, then [update](https://github.com/kryptokrona/kryptokrona/releases)

* Then, close and reopen xkrwallet and Kryptokronad.
* Type `reset` in xkrwallet after reopening your wallet file.
* It should start resetting your wallet, but the progress might not be immediately obvious - wait a while, and it should start counting up the blocks and printing out your transactions as it gets to them.

**Q: How do I backup my wallet?**

Open xkrwallet and type `export_keys`.\
Save the view and spend key somewhere safe, and you can use them to reimport your wallet if you lose it.

Q: My transactions are very slow

Try attemping a fusion transaction:

* Open up xkrwallet, and type `optimize`, then press enter.
* It will confirm if you want to optimize your wallet; it will take a bit. If you're fine with that, type `Y` and press enter again.

Your wallet is now being optimized. When it finishes, your transaction should be able to send

**Q: How do I send XKR?**

You can check [this out](../guides/wallets/Using-xkrwallet.md##sending-Kryptokrona-transactions) for steps on how to send XKR to someone.

**Q: How do I send money to exchanges / use payment ID?**

You can check [this out](../guides/wallets/Using-xkrwallet.md#payment-id) for steps on how to send XKR with the payment ID.

**Q: What is mixin?**

Mixin is how many times your transaction is "mixed" with others for obfuscation and privacy.\
Mixin is locked by the network to `7` as of block `620,000` and is not adjustable by the user; this is done to ensure that no one can send a non-private transaction(`0` mixin) or be a victim of the "Tall Poppy Syndrome" by using a high mixin compared to everyone else on the network.

**Q: How can I view my balance?**

If `Kryptokrona.exe` is fully synced, in xkrwallet, simply type `balance`.

**Q: How long does it take to sync Kryptokrona.exe?**

Currently it takes a couple of hours. This number will increase as more people use XKR and the blockchain gets larger. If you'd like to speed up the process, check out the question below.

**Q: Can I speed up the syncing of the blockchain?**

You can sync [with checkpoints](../guides/wallets/Using-Checkpoints.md) (only with xkrwallet) or use a [remote node](../guides/wallets/Using-Remote-Nodes.md)

**Q: Can I skip the syncing?**

Yes, you can currently use a remote node with xkrwallet and the desktopwallet. The keys stay on your PC, so it's secure. Check [this guide](../guides/wallets/Using-Remote-Nodes.md) for more information.

**Q: What does it mean if my balance is locked?**

This is a transfer which hasn't been confirmed by the network yet. It will move into your main balance shortly, generally after 3 minutes.

**Q: In xkrwallet.exe, I get an error `Error: failed to save new wallet: boost::filesystem::unique__path: Keyset as registered is invalid`. How can I fix it?**

This is caused by some broken Windows crypto keys. In the address bar in Windows Explorer, type `%AppData%/Microsoft/Crypto/RSA/`.

There should be a folder in there, with a long name, like `S-1-5-21-1416222650-108526586-4052533318-1000`.

Go into this folder and delete the files in there. Then reboot, and try again.

### Mining

#### General mining questions

**Q: How do I get started mining?**

You can check [this guide](../mining/mining.md)

**Q: I'm using a Mac, can I still mine?**

Yes, of course! We're working on a guide. You can install xmrig with [Brew](https://brew.sh/) and then use xmrig directly in your terminal. You can generate a config-file for xmrig [here](https://kryptokrona.org/mining) and then use: xmrig -c ../path/to/config.json to start mining.

**Q: I've started mining, how can I view my stats?**

Visit your pool's homepage. There should be a spot for you to put in your XKR address, and you can then view your hashrate, pending balance, payouts, and more.

**Q: Why is the hashrate on the pool website different to what is shown in my miner?**

The values will always be slightly different as it is an estimate, but if there is a large difference, it is likely you have just started mining.

Your hashrate is calculated over time, and so it will slowly go up to the correct level.

**Q: I've been mining for a while, but my pending balance hasn't gone up?**

On your pool website, check the time that the last block was found on your pool, and the average time to find a block.

Your stats will only update when your pool finds a block and it matures, so if your pool doesn't find blocks very often, you will have slower updating stats.

**Q: I've been mining, but the balance in my wallet hasn't gone up?**

To save money on fees, the pools send payouts in chunks. [Check your pool website for your pending balance](Frequently-Asked-Questions.md#q-i-ve-been-mining-for-a-while-but-my-pending-balance-hasn-t-gone-up).

**Q: Why are my results being rejected from the pool?**

You're using a incorrect algorithm. You should be using `cn-pico/trtl`.

**Q: I got banned from my mining pool. Why?**

If you submit lots of invalid shares, a pool might ban you. Possible reasons for invalid shares can be

* your hardware getting overworked,
* high ping to the pool,
* or your difficulty being set too low.

Try lowering any overclocks, choosing a pool closer to you or setting a higher difficulty port.

You should get unbanned after approximately 20 minutes. This is a good time to setup some backup pools!

**Q: Should I set up multiple pools?**

Yes, in case you get banned, or a pool goes down for some time, you can keep mining. A good amount to have would be at least three.

**Q: Where can I find a list of pools?**

[Here](../mining/pools.md) is a list. It also has other nifty stats like the pool's fee, minimum payout and server location.

**Q: What pool should I choose?**

There are a few factors to consider when choosing a pool.

* One is your ping, you can find this out by pinging the server in a command prompt by typing `ping example.org`, where `example.org` is the pool address.
*   Another is the hashrate of the pool. If you go on the pool's website, you can see how often they find blocks.

    If the pool takes a long time to find a block, your stats will take a long time to update.
*   Finally, the minimum payouts can be significant if you're a small miner.

    This is the amount you need to mine before you get paid. Most pools will list this under the "Payments" tab.

    You can check [this list](../mining/pools.md) of pools. It specifies each pool's minimum payout as well as server location.

**Q: How many hashes per second is good for my hardware?**

[http://monerobenchmarks.info/](http://monerobenchmarks.info/) is a good source for this. You can look up your [CPU](http://monerobenchmarks.info/searchCPU.php) and [GPU](http://monerobenchmarks.info/searchGPU.php). We also have our own benchmarks [here](https://kryptokrona.org/benchmarks).

**Q: I can't get the miner working, is there an easier way to mine?**

You can get some free XKR [here](https://kryptokrona.org/faucet).

Alternatively, you can hop onto the \[Discord]\[https://discord.gg/nRK5k7wYy8] if you're having issues and we'll help you out.

**Q: What is the miner executable / why isn't it working?**

This is a solo miner, which is CPU only. This means to gain any XKR, you have to find a block by yourself, which unless you have many powerful CPUs, is very unlikely.

We strongly recommend using a pool, and a miner such as NinjaRig.

Nevertheless, if you want to try it out, open a command prompt in the same directory, and run

```
./miner --address SEKR...
```

replacing `SEKR...` with your full XKR address.

You need to have `Kryptokrona` open and synced to use this miner, unlike conventional miners, where the pool hosts the daemon. You can also use a public node with the -r flag.

**Q: Is there a calculator to see how much XKR I'll mine per day?**

Your pool's homepage should have one - enter your hashrate and it'll give an estimate of how much XKR you'll mine per day.\
If there isn't, you can check one [here](https://explorer.kryptokrona.se).

### Paper Wallet / Cold Storage?

**Q: Wait, what's Cold Storage?**

The term "cold storage" refers to a wallet that has been created via an offline means.

The preferred way to do this is via a computer than has never ever been connected to the internet, commonly referred to as an air gapped device.

Why is this a thing? If done properly it means it is near impossible for the keys to be secretly intercepted since the data is never viewable by other compute devices.

You see above/elsewhere wallet files are being created via the wallet software, these files might be stored unencrypted, if unencrypted then the keys can be read by malicious software and balances of those wallets, transferred.

Thus to protect against that scenario you could transfer any XKR balance to one of these cold storage addresses. Please remember to keep secure/secret backups of your keys. If you lose the keys you lose any balance that was transferred to that wallet.

**Q: Can I make a paper wallet?**

Yes, you can view the guide [here](../guides/wallets/Making-a-Paper-Wallet.md)

**Q: I made a paper wallet, how do I use it?**

You can check out [this guide](../guides/wallets/Recovering-your-Wallet.md) for steps on how to import your paper wallet into a wallet of your choice(choose a wallet and import the keys).

**Q: Can I view the balance of my wallet online?**

A: Due to Kryptokrona being a cryptonote-based coin(private), this is not possible.

It should be possible in the future to allow users to give away just their Private View Key to view transactions, but this hasn't been implemented by anyone so far, and would allow that website to see every transaction that you make.

### Other

**Q: How can I get some XKR?**

There are multiple ways to acquire XKR, for example:

* Mining - see [here](../mining/mining.md)
* Bounties - Bounties for developing XKR software, spreading the word of XKR, and many other things are often posted in the #bounties channel on \[Discord]\[https://discord.gg/nRK5k7wYy8]. Check the pinned messages for current bounties.
* Tips - In the Kryptokrona discord we often tip each other, especially if you make spicy memes in the `#memes` channel.
* Buy at an exchange - Check out [this guide](broken-reference).

**Q: Are there any mobile wallets?**

There is currently an Android wallet available in the (Play Store)\[https://play.google.com/store/apps/details?id=com.xkr].

**Q: Where is the blockchain stored?**

On Windows, it is in `%APPDATA%/Kryptokrona`. On Mac and Linux, it is in `~/.kryptokrona`.

**Q: Is there a block explorer?**

Yes, the official one is

* https://explorer.Kryptokrona.se

**Q: How do I make sure a pool isn't forked?**

Check what network block height it is reporting, compared to other sources.

**Q: I have a question which wasn't answered here, what should I do?**

\[Join the Discord server]\[https://discord.gg/nRK5k7wYy8], and come to the `#help` channel, we'll try and fix any issues.
