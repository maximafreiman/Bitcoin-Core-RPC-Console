Kata Perintah dalam RPC Console
---
Yo.. balik lagi dan selamat pagi siang sore malam, kawan-kawan sekalian. Jadi di bab sebelumnya kita sudah mengenal salah satu fitur pada node Bitcoin berbasis software GUI (Graphic User Interface, buat yang belum paham bisa kembali ke bab 1). Nah sekarang, kita akan kenalan dengan beberapa kata perintah yang bisa kita pakai untuk cari informasi atau data pada Bitcoin network, entah secara real-time, atau historis.

Nah jadi ibaratnya gini, kalau RPC Console itu semacam 'browser' atau tempat untuk cari informasi di node, maka kata perintah atau sebutannya 'Command Prompts' adalah kata-kata kunci yang kita pakai untuk cari informasi tertentu secara spesifik di node.

Nah, sekarang pertanyaannya, berapa kata perintah atau *Command Prompts* yang ada pada node Bitcoin? Well, banyak. Ya, cukup banyak bahkan menurut update Bitcoin Core terbaru, bisa sampai ratusan.

Nih, update terbaru, kebetulan aku pakai Bitcoin Knots (ya Knots ini adalah fork dari Core, betul sekali) ada 174 Command Prompts:


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

Suer, masih banyak dan aku nggak bisa ketik satu-satu, hehe. Cuma apakah perlu untuk dipelajari semuanya? Tergantung, kalau temen-temen disini mau jadi seorang developer pada bitcoin, ya silakan pelajari semuanya. Cuma untuk kali ini dan seterusnya aku bakal tulis 20 saja yang sudah cukup untuk dipakai node user untuk semua kalangan. Entah yang masih pemula atau yang udah jago banget dalam memahami ekosistem Bitcoin.

So, berikut ini adalah 20 Command Prompts yang udah dipilah-pilah dan bisa kita pakai di RPC Console node Bitcoin kita:

---

**==BUAT CARI INFORMASI BLOCK DAN BLOCKCHAIN (ATAU TIMECHAIN SEBENERNYA) TERBARU***

1. `getblockchaininfo`

Fungsi: Menampilkan kondisi lengkap blockchain di node kita. Command ini memberi gambaran apakah node sudah sinkron dengan blockchain terbaru atau belum, sedang di mainnet/testnet, apakah node kita pruned, dan seberapa besar data blockchain yang sudah tersimpan.
Intinya: Ini adalah “dashboard kesehatan” node kita.

2. `getbestblockhash`

Fungsi: Menampilkan hash dari blok paling terbaru. Bitcoin menyusun data dalam bentuk rantai blok. Command ini menunjukkan “ujung rantai” saat ini, yaitu blok terakhir yang dianggap valid oleh node kita.

Intinya: Ini adalah penanda posisi terbaru blockchain.

3. `getblockcount`

Fungsi: Menampilkan jumlah blok dari genesis sampai sekarang. Setiap blok punya nomor (height). Command ini menunjukkan node kita sedang ada di blok ke berapa.

Intinya: Ini adalah “jumlah aktual” blockchain dalam bentuk angka.

4. `getblock <blockhash>`

Fungsi: Menampilkan isi lengkap dari sebuah blok. Kita bisa melihat transaksi di dalam blok, waktu dibuat, ukuran, miner, dan berbagai data teknis lainnya.

Intinya: Ini seperti “membuka isi kotak” dari satu blok Bitcoin.

5. `getdifficulty`

Fungsi: Menampilkan tingkat kesulitan mining saat ini. Semakin tinggi angkanya, semakin sulit bagi miner menemukan blok baru. Ini menyesuaikan otomatis agar rata-rata blok tetap muncul setiap ±10 menit.

Intinya: Ini adalah pengukur seberapa keras kerja miner di jaringan.

**==BUAT CARI INFORMASI TENTANG KONDISI NODE DAN NETWORK**

6. `getnetworkinfo`

Fungsi: Menampilkan informasi jaringan node. Menunjukkan versi sfotware Bitcoin Core atau Knots yang kita pakai, fitur jaringan yang aktif, dan status koneksi.

Intinya: Ini adalah identitas node kita di dunia Bitcoin.

7. `getpeerinfo`

Fungsi: Menampilkan daftar node lain yang terhubung ke node kita. Kita bisa lihat IP, negara, latency, dan apakah peer itu inbound atau outbound. Inbound itu peer node lain yang nyambung ke kita, Kalau outbound, ya sebaliknya. Kita yang sambung ke peer node orang lain.

Intinya: Ini adalah “daftar teman” node Kita di jaringan.

8. `getconnectioncount`

Fungsi: Menampilkan jumlah koneksi aktif. Semakin banyak koneksi, semakin kuat node kita dalam menerima dan menyebarkan data.

Intinya: Ini adalah jumlah jalur komunikasi node Kita.

9. `ping`

Fungsi: Menguji koneksi ke peer. Node Kita mengirim sinyal ke peer untuk memastikan mereka masih aktif dan responsif.

Intinya: Ini adalah “cek apakah temanmu masih online.”

10. `getnettotals`

Fungsi: Menampilkan total data yang dikirim dan diterima. Kita bisa lihat seberapa besar kontribusi node Kita dalam menyebarkan data blockchain.

Intinya: Ini adalah jejak kontribusi bandwidth node Kita.

**==UNTUK CEK STATUS MEMPOOL DAN TRANSAKSI**

11. `getrawmempool`

Fungsi: Menampilkan daftar transaksi yang belum masuk blok. Mempool adalah “ruang tunggu” transaksi sebelum ditambang. Command ini menunjukkan antreannya.

Intinya: Ini adalah antrian transaksi Bitcoin.

12. `getmempoolinfo`

Fungsi: Menampilkan kondisi mempool. Kita bisa lihat ukuran mempool, jumlah transaksi, dan tekanan fee.

Intinya: Ini adalah indikator macet atau lancarnya jaringan.

13. `getrawtransaction "txid"`

Fungsi: Mengambil data mentah sebuah transaksi. Menampilkan transaksi dalam format teknis (hex) langsung dari jaringan atau blockchain.

Intinya: Ini adalah mengambil “bentuk asli” transaksi.

14. `decoderawtransaction "hex"`

Fungsi: Mengubah transaksi mentah jadi format yang bisa dibaca manusia. Kita bisa lihat input, output, nilai BTC, dan alamat tujuan.

Intinya: Ini adalah penerjemah bahasa mesin ke bahasa manusia.

15. `sendrawtransaction "hex"`

Fungsi: Mengirim transaksi ke jaringan Bitcoin. Setelah transaksi ditandatangani, command ini akan menyebarkannya ke node lain.
Intinya: Ini adalah “cara menyebarkan ke dunia Bitcoin.”

**==UNTUK INFORMASI WALLET DAN MINING**

16. `getwalletinfo`

Fungsi: Menampilkan status wallet. Menunjukkan saldo, jumlah transaksi, dan apakah wallet terkunci atau tidak.

Intinya: Ini adalah dashboard dompet Kita.

17. `getnewaddress`

Fungsi: Membuat alamat Bitcoin baru. Alamat baru ini bisa Kita pakai untuk menerima BTC dengan privasi lebih baik.

Intinya: Ini adalah generator rekening Bitcoin.

18. `getbalance`

Fungsi: Menampilkan saldo wallet. Menunjukkan berapa BTC yang bisa kita gunakan atau kirim.

Intinya: Ini adalah cek isi dompet.

19. `sendtoaddress "address" amount`

Fungsi: Mengirim BTC ke alamat lain. Node kita akan membuat, menandatangani, dan mengirim transaksi ke jaringan.

Intinya: Ini adalah tombol “kirim uang” Bitcoin.

20. `getmininginfo`

Fungsi: Menampilkan info seputar mining.
Menunjukkan hashrate jaringan, difficulty, dan status mining node kita.

Intinya: Ini adalah status produksi blok Bitcoin.
