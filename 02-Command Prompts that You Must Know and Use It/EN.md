Command Prompts in Bitcoin Node RPC Console
---
Yo… welcome back, and good morning, afternoon, evening, or night, my friends. So, in the previous chapter, we got to know one of the features of a Bitcoin node based on GUI software (Graphical User Interface. If you’re not familiar with it, you can go back to Chapter 1). Now, we’re going to get acquainted with several command keywords that we can use to search for information or data on the Bitcoin network, whether in real time or historically.

So think of it like this: if the RPC Console is like a “browser” or a place to look for information on your node, then the commands — or what we call “Command Prompts” — are the specific keywords we use to search for particular information inside the node.

Now, the question is: how many commands are there on a Bitcoin node? Well, a lot. Yes, quite a lot. In fact, according to the latest Bitcoin Core update, there can be hundreds of them.

Here’s the latest update: I happen to be using Bitcoin Knots (yes, Knots is a fork of Core, that’s absolutely right), and it has 174 command prompts:

`dumptxoutset "path" ( "type" {"format":["txid","vout","value","coinbase","height","scriptPubKey",...],"rollback":n,"show_header":bool,"separator":"str",...} )`

`getbestblockhash`

`getblock "blockhash" ( verbosity )`

`getblockchaininfo`

`getblockcount`

`getblockfilter "blockhash" ( "filtertype" )`

`getblockfrompeer "blockhash" peer_id`

`getblockhash height`

`getblockheader "blockhash" ( verbose )`

`getblockstats hash_or_height ( stats )`

`getchainstates`

`getchaintips`

`getchaintxstats ( nblocks "blockhash" )`

Honestly, there are still a lot of them, and I can’t type them all out one by one, haha. But do you really need to learn all of them? It depends. If you want to become a Bitcoin developer, then sure, go ahead and study them all. But for now and going forward, I’m only going to list 20 commands which are more than enough for node users of all levels, whether you’re a complete beginner or already highly skilled in understanding the Bitcoin ecosystem.

So, here are 20 Command Prompts that have been carefully selected and that we can use in our Bitcoin node’s RPC Console:
---

**==TO FIND THE LATEST BLOCK AND BLOCKCHAIN INFORMATION (OR “TIMECHAIN,” TO BE MORE ACCURATE)***

1. `getblockchaininfo`

Function: Displays the full status of the blockchain on our node. This command gives an overview of whether the node is synchronized with the latest blockchain, whether it’s running on mainnet or testnet, whether the node is pruned, and how much blockchain data has been stored.

In short: This is the “health dashboard” of our node.

2. `getbestblockhash`

Function: Displays the hash of the most recent block. Bitcoin structures its data as a chain of blocks. This command shows the current “tip of the chain,” which is the latest block considered valid by our node.

In short: This is the marker for the latest position of the blockchain.

3. `getblockcount`

Function: Displays the total number of blocks from the genesis block up to the present. Each block has a number (its height). This command shows which block height our node is currently at.

In short: This is the “current count” of the blockchain in numerical form.

4. `getblock <blockhash>`

Function: Displays the full contents of a block. We can see the transactions inside the block, the time it was created, its size, the miner, and various other technical details.

In short: This is like “opening the box” of a single Bitcoin block.

5. `getdifficulty`

Function: Displays the current mining difficulty. The higher the number, the harder it is for miners to find a new block. This adjusts automatically so that blocks continue to be found roughly every ±10 minutes.

In short: This is a measure of how hard miners are working on the network.

**==TO FIND INFORMATION ABOUT THE STATUS OF THE NODE AND THE NETWORK**

6. `getnetworkinfo`

Function: Displays network information about the node. It shows the version of Bitcoin Core or Knots you’re running, the active network features, and the connection status.

In short: This is the node’s identity in the Bitcoin world.

7. `getpeerinfo`

Function: Displays a list of other nodes connected to our node. We can see their IP addresses, countries, latency, and whether each peer is inbound or outbound. Inbound means other nodes are connecting to us; outbound means we are the ones connecting to other nodes.

In short: This is the “friends list” of our node on the network.

8. `getconnectioncount`

Function: Displays the number of active connections. The more connections you have, the stronger your node is at receiving and propagating data.

In short: This is the number of communication channels your node has.

9. `ping`

Function: Tests the connection to a peer. Our node sends a signal to the peer to make sure they are still active and responsive.

In short: This is a “check to see if your friend is still online.”

10. `getnettotals`

Function: Displays the total amount of data sent and received. We can see how much our node has contributed to propagating blockchain data.

In short: This is the bandwidth contribution footprint of our node.

**==UNTUK CEK STATUS MEMPOOL DAN TRANSAKSI**

11. `getrawmempool`

Function: Displays the list of transactions that have not yet been included in a block. The mempool is the “waiting room” for transactions before they are mined. This command shows that queue.

In short: This is the Bitcoin transaction queue.

12. `getmempoolinfo`

Function: Displays the current state of the mempool. We can see the mempool size, the number of transactions, and the level of fee pressure.

In short: This is an indicator of how congested or smooth the network is running.

13. `getrawtransaction "txid"`

Function: Retrieves the raw data of a transaction. It displays the transaction in its technical (hex) format directly from the network or the blockchain.

In short: This is fetching the “original form” of a transaction.

14. `decoderawtransaction "hex"`

Function: Converts a raw transaction into a human-readable format. We can see the inputs, outputs, BTC amounts, and destination addresses.

In short: This is a translator from machine language to human language.

15. `sendrawtransaction "hex"`

Function: Broadcasts a transaction to the Bitcoin network. After the transaction is signed, this command propagates it to other nodes.

In short: This is the “way to release it into the Bitcoin world.”

**==FOR CHECKING WALLET AND MINING INFORMATION**

16. `getwalletinfo`

Function: Displays the wallet status. It shows the balance, the number of transactions, and whether the wallet is locked or unlocked.

In short: This is the dashboard of our wallet.

17. `getnewaddress`

Function: Generates a new Bitcoin address. This new address can be used to receive BTC with better privacy.

In short: This is a Bitcoin account generator.

18. `getbalance`

Function: Displays the wallet balance. It shows how much BTC we can use or send.

In short: This is a wallet balance check.

19. `sendtoaddress "address" amount`

Function: Sends BTC to another address. Our node creates, signs, and broadcasts the transaction to the network.

In short: This is the Bitcoin “send money” button.

20. `getmininginfo`

Function: Displays mining-related information. It shows the network hashrate, difficulty, and the mining status of our node.

In short: This is the block production status of Bitcoin.


Alright, that’s it for the command prompts we can apply at the beginner stage. Later on, I might also share some additional prompts that we can use. That’s all for now, thank you.
