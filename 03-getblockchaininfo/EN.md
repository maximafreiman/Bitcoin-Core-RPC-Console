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

Waktu dalam satuan detik, kapan block ini tercipta. Dengan acuan UTC (Terhitung sejak Unix epoch (1 Januari 1970 00:00:00 UTC) sebagai titik referensi waktu yang disepakati.)

--

**mediantime": 1769343081**

Mediantime adalah timestamp median dari 11 block sebelumnya yang digunakan node sebagai referensi waktu minimum untuk memvalidasi field time pada block baru. Kenapa 11? Untuk cari median (nilai tengah) pasti pakai kombinasi angka dengan batas ganjil, dan antara detik saat block terbaru tercipta dengan detik saat 11 block sebelumnya tercipta, itu sudah ideal. 1 hingga sebelas, angka tengahnya adalah 6. Maka median time diambil dari saat detik 6 block sebelumnya tercipta. Angka 6 muncul dari nilai tengah 11, seperti poin tadi. Bukan muncul begitu saja.

--

**verificationprogress": 0.9999983113513633**

Progress verifikasi seluruh PoW, rantai block, transaksi, dan UTXO sesuai aturan konsensus hingga ke block terbaru. Disini, terlihat proses verifikasinya adalah 0.999..., artinya adalah, node kita sudah 99% progressnya.

--

**"initialblockdownload": false,**

Indikator yang menunjukkan apakah node kita masih dalam fase sinkronisasi awal blockchain atau sudah mengikuti jaringan secara normal. Kalau `true`, berarti masih proses. Kalau `false` berarti proses IBD sudah selesai dan sedang melakukan verifikasi semua hal pada block terbaru.

--

**size_on_disk": 815042789810,**

total ukuran data blockchain yang sudah disimpan node kita di disk kita (block, index, dan file terkait), dalam byte. 815042789810 bytes artinya, atau kalau dikonversi lagi = 815 GB.

--

**pruned": false,**

Ini menunjukkan apakah node kamu berjalan dalam mode pruning (menghapus block lama) atau menyimpan blockchain penuh. `false` artinya full node arsip, menyimpan semua block dari genesis sampai sekarang di disk. Kalau `true` artinya pruned node. Hanya menyimpan block terbaru (sesuai pengaturan yang kita set), block lama dihapus setelah diverifikasi.

--

**warnings": []**

Ini adalah bagian peringatan pada node kita, kalau kosong, berarti aman. Kemunculan peringatan ini tergantung pada alert apa yang muncul nanti, entah misalnya low disk, atau ada chain fork, dll.

----------------------------------------------------------------------------------------------------

So, ini adalah bagaimana cara kita melakukan verifikasi dasar pada kondisi terbaru aktivitas node dalam proses verifikasi blockchain. And yes, sekalian kita bahas informasi apa saja yang muncul. Sekian, terima kasih.


