Kata Perintah dalam RPC Console
---
Yo.. balik lagi dan selamat pagi siang sore malam, kawan-kawan sekalian. Jadi di bab sebelumnya kita sudah mengenal salah satu fitur pada node Bitcoin berbasis software GUI (Graphic User Interface, buat yang belum paham bisa kembali ke bab 1). Nah sekarang, kita akan kenalan dengan beberapa kata perintah yang bisa kita pakai untuk cari informasi atau data pada Bitcoin network, entah secara real-time, atau historis.

Nah jadi ibaratnya gini, kalau RPC Console itu semacam 'browser' atau tempat untuk cari informasi di node, maka kata perintah atau sebutannya 'Command Prompts' adalah kata-kata kunci yang kita pakai untuk cari informasi tertentu secara spesifik di node.

Nah, sekarang pertanyaannya, berapa kata perintah atau *Command Prompts* yang ada pada node Bitcoin? Well, banyak. Ya, cukup banyak bahkan menurut update Bitcoin Core terbaru, bisa sampai ratusan.

Nih, update terbaru, kebetulan aku pakai Bitcoin Knots (ya Knots ini adalah fork dari Core, betul sekali) ada 174 Command Prompts:

== Blockchain ==

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

