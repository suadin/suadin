# Crypto Currency Mining
On this page I will summarize my experiances with crypto currency mining.

## Getting Started
I started with [nicehash](https://www.nicehash.com/): create wallet, download cpu miner, whitelist miner on windows defender, install & start miner, get after few minutes first coins and after few hours first cents. Less effort, potential security risk, less profit.

## Basics

Mining keywords:
* [Blockchain](https://www.simplilearn.com/tutorials/blockchain-tutorial/what-is-blockchain): record of transactions managed by decentral network
* Algorithm: solves jobs with calculation steps to verify blockchain, examples: [RandomXmonero](https://www.nicehash.com/algorithm/randomxmonero), [CryptoNight](https://academy.bit2me.com/en/what-is-the-algorithm-of-cryptonight-mining/), [MTP](https://github.com/firoorg/firo/wiki/What-is-MTP-(Merkle-Tree-Proof)-and-why-is-it-an-ideal-Proof-of-Work-algorithm%3F)
* Miner: executes algorithm to verify blockchain, examples: [XMRig](https://github.com/xmrig/xmrig), [cpuminer](https://github.com/tpruvot/cpuminer-multi), [ccminer](https://github.com/tpruvot/ccminer/tree/linux)
* H/s: Hashs per seconds are the unit to measure performance of miners
* Pools: set of miners, miner which solves job first get coins, examples: [nicehash.com](https://www.nicehash.com/stratum-generator), [2miners.com](https://firo.2miners.com/de/help)
* Protocol: communication rules between miners and pool, example: [Stratum](https://de.bitcoinwiki.org/wiki/Stratum-Mining-Protokoll)
* Wallet: stores mined coins, example: [nicehash](https://www.nicehash.com), [firo](https://firo.org/guide/how-to-mine-firo.html)

Getting started setup: wallet:nicehash, protocol:stratum, pool:nicehash, ~1000H/s, miner:xmrig, algo:randomxmonero.

## Linux Server Setup
For 24/7 tried to setup miners on linux server:
* with docker: very easy but low/no profit (~40H/s), images: [nicehash-miner](https://hub.docker.com/r/caspernaudts/nicehash-miner), [cpuminer](https://hub.docker.com/r/tpruvot/cpuminer-multi), [xmrig](https://hub.docker.com/r/xmrig/xmrig)
* native: not all guides work, time intensive, low/no profit (~40H/s), one of the better guides [here](https://vpsfix.com/7785/install-xmrig-cpu-miner-on-ubuntu-16-04-with-cli/)

Unfortunately my linux server is a V-Server, I think therefore it is slower than my local physical machine (25 times faster!).

## GPU Setup
CPU-Mining work weel, GPU should be better. But my GPU (NVIDIA Geforce GMX 760) is not supported by NiceHash QuickMiner, error: No compatible hardware detected!

Found following [GeForce GTX 760](https://www.betterhash.net/NVIDIA-GeForce-GTX-760-mining-profitability-204268.html) profitability forecast (~1.40 MH/s), much faster than CPU [Intel(R) Core(TM) i5-4670K CPU @ 3.40GHz](https://www.betterhash.net/Intel(R)-Core(TM)-i5-4670K-CPU-@-3.40GHz-mining-profitability-864465.html) profitability forecast (~1318.29 H/s).

Recommended stack: wallet:firo, protocol:stratum, pool:2miners, miner:ccminer, algo:mtp. Miner runs but throws error: cudaErrorInvalidValue. Guess: need build for my [GPU compute version 3.0](https://cryptomining-blog.com/tag/compute-3-0/). Guide for [support older cuda gpus on ccminer](https://forum.getpimp.org/topic/222/ccminer-is-not-supporting-the-older-cuda-gpus-by-default-compute-capability-3-5-and-smaller) found, but sources are not buildable. Stop further effort to save time.

## Conclusion
Getting started capture was cool because was quick & it works, some cents per week, some euros per months. But security risk exists and german power is more expensive than earned coins. Better have a seperate machine which runs as fix cost, unfortunately V-Server are very slow and therefore no options.

Optimize mining:
* host in a country with less power cost, not germany
* use special [hardware](https://bitcoinvox.com/best-bitcoin-mining-hardware/) to optimize profit/lost