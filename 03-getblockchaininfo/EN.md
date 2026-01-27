getblockchaininfo
---
Okay, so let’s first try going to the Command Prompt, friends, using `getblockchaininfo`.
`getblockchaininfo` is an RPC command in Bitcoin Core / Bitcoin Knots that displays information about the current state of the local blockchain being run by our node.

Let’s explore what kind of information we can get when using this command.
For instructions on how to open the RPC Console, please refer to Chapter 1. (https://github.com/maximafreiman/Bitcoin-Core-RPC-Console/blob/main/01-Introduction/ID.md).


Okay, so first of all, it’s quite simple. In the input field at the bottom, just type `getblockchaininfo`. All lowercase, with no spaces.

<img width="1366" height="726" alt="1" src="https://github.com/user-attachments/assets/e2a3d606-c367-4e4f-9822-71601a9b240d" />

Then, the output will appear like this. (This is blockchain data as of January 25, 2026, at 13:45 UTC.)

<img width="1366" height="725" alt="2" src="https://github.com/user-attachments/assets/6212c3e8-26cf-4a35-a3c1-bb2b2c8f9951" />

Let’s break down the data shown here and examine everything in detail in this single article.

  `"chain": "main",`
  
  `"blocks": 933732,`
  
  `"headers": 933732,`
  
  `"bestblockhash": "000000000000000000001ecd8963323c01c98909d02600c2c4e230a7f1856598",`
  
  `"bits": "1701fca1",`
  
  `"target": "00000000000000000001fca10000000000000000000000000000000000000000",`
  
  `"difficulty": 141668107417558.2,`
  
  `"time": 1769348377,`
  
  `"mediantime": 1769343081,`
  
  `"verificationprogress": 0.9999983113513633,`
  
  `"initialblockdownload": false,`
  
  `"chainwork": "000000000000000000000000000000000000000109def53174aa6446ccc9cab9",`
  
  `"size_on_disk": 815042789810,`
  
  `"pruned": false,`
  
  `"warnings": [`
  
  `]`

`}`

--

**"chain": "main"**

This means our node is connected to the Bitcoin Mainnet.
This is the real Bitcoin network, not:
- test (testnet)
- regtest (local)
All transactions and blocks on this network are economically real.

--

**"blocks": 933732**

This is the total number of blocks that your node has already stored and fully validated.

--

**"headers": 933732**

This is the number of block headers known by the node.

A block header is the block’s metadata (hash, timestamp, target, nonce, etc.).
Headers are usually downloaded faster than full blocks.
Even so, the total count should exactly match the blocks value.

--

**"bestblockhash": 000000000000000000001ecd8963323c01c98909d02600c2c4e230a7f1856598**

This is the hash (a unique code derived from the block header data, combined into a single cryptographic value) of the latest block at the tip of the chain that our node considers valid.

--

**"bits": "1701fca1"**

bits is a compact representation of the proof-of-work target that stores the maximum valid hash threshold in 4 bytes within the block header.

--

**"target": "00000000000000000001fca10000000000000000000000000000000000000000",**

The target is a 256-bit threshold number that determines whether a block hash is valid or not.
A node will only accept a block if its hash is lower than the target. If it is higher, the block is rejected.
--

**difficulty": 141668107417558.2**

Difficulty is a relative value that shows how much smaller the current target is compared to Bitcoin’s original target, describing how hard it is for the network to mine a block.

(Bits, target, and difficulty are three closely related concepts in the block mining process. They will be explained in a separate article.)

--

**time": 1769348377**

This is the time, expressed in seconds, when the block was created, using UTC as the reference.
It is calculated from the Unix epoch (January 1, 1970, 00:00:00 UTC) as the agreed-upon time reference.

--

**mediantime": 1769343081**

Mediantime is the median timestamp of the previous 11 blocks, which the node uses as the minimum time reference when validating the time field of a new block. Why 11? To determine a median (the middle value), an odd number of samples is required. The range between the timestamp of the newest block and those of the previous 11 blocks is considered ideal. With 11 values, the middle position is the 6th value. Therefore, the median time is taken from the timestamp of the block that was mined 6 blocks before the current one. The number 6 does not appear arbitrarily, it comes directly from the midpoint of 11, as explained above.

--

**verificationprogress": 0.9999983113513633**

This represents the verification progress of the entire proof-of-work, block chain, transactions, and UTXO set according to consensus rules up to the latest block. Here, the verification progress is shown as 0.999…, which means our node has completed approximately 99% of the verification process.

--

**"initialblockdownload": false,**

This indicator shows whether our node is still in the initial blockchain synchronization phase or has already caught up and is operating normally with the network.

If it is set to `true`, the node is still in the process.
If it is `false`, the Initial Block Download (IBD) process is complete, and the node is now validating everything on the latest blocks.

--

**size_on_disk": 815042789810,**

This is the total size of blockchain data that our node has stored on disk (blocks, indexes, and related files), measured in bytes. 815,042,789,810 bytes, which converts to approximately 815 GB.

--

**pruned": false,**

This indicates whether your node is running in pruning mode (removing old blocks) or storing the full blockchain. If it is set to `false`, the node is an archival full node, storing all blocks from genesis to the present on disk. If it is `true`, the node is a pruned node, which only keeps the most recent blocks (according to the configured limit), and older blocks are deleted after verification.

--

**warnings": []**

This is the warning section of our node. If it is empty, it means everything is operating safely. Warnings will appear here depending on the situation, such as low disk space, a detected chain fork, or other node-related alerts.

----------------------------------------------------------------------------------------------------

So, this is how we perform a basic verification of our node’s latest activity during the blockchain verification process. And yes, we also covered the key information that appears there.

That’s all for this session. Thank you.


