getblockchaininfo
---
Oke, jadi kita coba ke Command Prompt pertama ya kawan-kawan, yaitu 'getblockchaininfo'. getblockchaininfo adalah RPC command di Bitcoin Core / Bitcoin Knots yang menampilkan informasi kondisi blockchain lokal yang sedang dijalankan oleh node kita.

Kita coba ulik disini dapat informasi apa saja begitu kita pakai command prompt ini. Mengenai bagaimana cara buka RPC Console, bisa buka bab 1 (https://github.com/maximafreiman/Bitcoin-Core-RPC-Console/blob/main/01-Introduction/ID.md).


Oke, jadi, pertama-tama, cukup simple. Di kolom bagian bawah, bisa ketik `getblockchaininfo`. Huruf kecil semua, tanpa spasi.

<img width="1366" height="726" alt="1" src="https://github.com/user-attachments/assets/e2a3d606-c367-4e4f-9822-71601a9b240d" />

Maka, hasilnya akan keluar seperti ini. (Ini adalah data blockchain per tanggal 25 Januari 2026, jam 20:45 WIB)

<img width="1366" height="725" alt="2" src="https://github.com/user-attachments/assets/6212c3e8-26cf-4a35-a3c1-bb2b2c8f9951" />

Yuk kita coba bedah data yang ada disini dan kita telaah semuanya dalam 1 artikel ini.

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
  
  "warnings": [
  ]
}

--

**"chain": "main"**

Artinya node kita terhubung ke Mainnet Bitcoin. Ini jaringan Bitcoin asli, bukan:
- test (testnet)
- regtest (lokal)
Semua transaksi & blok di sini “nyata” secara ekonomi

--

**"blocks": 933732**

Ini adalah jumlah blok yang sudah kamu simpan dan validasi penuh

--

**"headers": 933732**

Jumlah block header yang diketahui node

Header = metadata blok (hash, waktu, target, nonce, dll)
Biasanya lebih cepat didownload daripada blok penuh. Meski begitu, jumlah pasti sama dengan "blocks"

--

**"bestblockhash": 000000000000000000001ecd8963323c01c98909d02600c2c4e230a7f1856598**

Ini adalah hash (sebuah kode unik yang berasal dari data header block, dijadikan satu data dalam bentuk kode acak), dari blok terbaru di ujung rantai yang node kita anggap valid.

--

**"bits": "1701fca1"**

bits adalah format ringkas dari target proof-of-work yang menyimpan batas maksimum hash valid dalam 4 byte di header blok.

--

**"target": "00000000000000000001fca10000000000000000000000000000000000000000",**

Target adalah angka batas 256-bit yang menentukan apakah sebuah hash blok valid atau tidak.
Node akan menerima blok hanya jika: hash lebih kecil dari target. Kalau sebaliknya, maka blok ditolak.

--

**difficulty": 141668107417558.2**

Difficulty adalah angka perbandingan yang menunjukkan seberapa kecil target sekarang dibanding target awal Bitcoin, untuk menggambarkan seberapa susah jaringan menambang blok.

(Bits, target, dan difficulty adalah 3 hal yang sangat berkaitan dalam proses mining suatu blok. Dijelaskan dalam artikel terpisah).
