### 🗂️ Activity Selection Problem (ASP)

## 📖 Ringkasan Umum

**Activity Selection Problem (ASP)** adalah salah satu contoh masalah optimasi klasik dalam ilmu komputer. Tujuannya adalah memilih sebanyak mungkin aktivitas yang **tidak saling tumpang tindih**, dengan mengacu pada waktu mulai dan waktu selesai masing-masing aktivitas.

Masalah ini sering muncul di dunia nyata, seperti:
- 📅 Penjadwalan kelas atau ruangan
- 💼 Wawancara kerja
- 🛠️ Pengelolaan sumber daya

---

## ❓ Apa Syaratnya?

Untuk menyelesaikan ASP, kita harus memenuhi dua kondisi penting:

- ⏰ **Tidak boleh ada dua aktivitas yang waktunya bertabrakan**
- 👤 **Hanya satu aktivitas yang dapat dilakukan dalam satu waktu**

---

## 💡 Solusi: Greedy Algorithm

**Greedy Algorithm** adalah metode penyelesaian yang membuat keputusan optimal pada setiap langkah kecil (lokal), dengan harapan akan menghasilkan hasil yang optimal secara keseluruhan (global).

### Mengapa ASP Cocok dengan Greedy?
✔️ Aktivitas yang selesai lebih awal memberi ruang untuk aktivitas selanjutnya  
✔️ Sifat *lokal optimal* dari greedy terbukti mengarah ke solusi *global optimal*

---

## 🛠️ Langkah-langkah Penyelesaian ASP

Berikut strategi umum untuk menyelesaikan ASP menggunakan algoritma greedy:

1. 📊 **Urutkan semua aktivitas berdasarkan waktu selesai secara menaik**
2. ✅ **Pilih aktivitas pertama** (yang selesai paling cepat)
3. 🔄 Untuk setiap aktivitas berikutnya:
   - Pilih jika waktu **mulai ≥ selesai aktivitas terakhir yang dipilih**
4. 🔚 Ulangi hingga akhir daftar

---

## 🧪 Contoh Kasus

Diberikan aktivitas berikut:

| Aktivitas | Mulai | Selesai |
|-----------|-------|---------|
| A         | 1     | 4       |
| B         | 3     | 5       |
| C         | 0     | 6       |
| D         | 5     | 7       |
| E         | 8     | 9       |
| F         | 5     | 9       |

### ✔️ Hasil Optimal:
Aktivitas yang dipilih: **A, D, E**  
Jumlah maksimal: **3 aktivitas**

---


### 🎒 Fractional Knapsack – Strategi Greedy untuk Nilai Maksimal

> *"Kadang, membawa setengah batangan emas lebih baik daripada tidak membawa sama sekali."*

---

## 📌 Apa itu Fractional Knapsack?

**Fractional Knapsack** adalah varian dari masalah knapsack (ransel) di mana kamu **boleh mengambil sebagian dari suatu barang** untuk memaksimalkan total nilai yang dibawa, tanpa melebihi kapasitas tas.

Berbeda dari versi 0/1 (yang hanya memperbolehkan mengambil barang secara utuh), di sini kamu bisa ambil setengah, sepertiga, atau berapa pun yang muat dalam kapasitas yang tersedia.

---

## 🎯 Tujuan Masalah

Kita memiliki:
- Sebuah tas dengan **kapasitas terbatas** (misalnya 50 kg)
- Sekumpulan barang, masing-masing punya **berat dan nilai**

Tugas kita:
- Memilih barang atau bagian dari barang untuk dimasukkan ke tas
- Memaksimalkan **total nilai** dari barang-barang tersebut

---

## ⚙️ Strategi Penyelesaian

Masalah ini diselesaikan dengan pendekatan **algoritma greedy**, yaitu:
1. Hitung **rasio nilai per berat** dari setiap barang (`value / weight`)
2. Urutkan barang berdasarkan rasio tersebut (dari yang tertinggi)
3. Ambil barang dari yang paling menguntungkan hingga kapasitas habis
4. Jika tidak muat seluruhnya, ambil **sebagian proporsional** dari sisanya

---

## 💡 Ilustrasi Sederhana

Misalnya kamu punya:
- Barang A: 10 kg, Rp60
- Barang B: 20 kg, Rp100
- Barang C: 30 kg, Rp120

Kamu hanya punya kapasitas 50 kg. Dengan strategi greedy, kamu akan:
- Ambil A (penuh) → 10 kg
- Ambil B (penuh) → 20 kg
- Ambil C (sebagian: 20/30) → 20 kg
- Total nilai: **Rp240**

---

## 🧠 Kenapa Penting?

- Digunakan dalam pengambilan keputusan optimal
- Konsep dasar untuk alokasi sumber daya terbatas
- Cocok untuk dipelajari saat memahami algoritma greedy

---

## ⏱️ Kompleksitas Waktu

- **O(n log n)** – karena proses pengurutan berdasarkan rasio
- Efisien untuk kasus besar jika dibandingkan dengan 0/1 knapsack

---

## 🖋️ Catatan Akhir

Fractional Knapsack adalah pengantar yang bagus untuk memahami konsep greedy. Tidak semua masalah bisa diselesaikan dengan pendekatan ini, tapi ketika bisa—hasilnya sangat optimal dan elegan.

---
title: "Huffman Coding"
date: 2025-06-10 00:00:)) +0800
categories: [Kelompok 3]
tags: [Hello World]
---

### 🧠 Huffman Coding – Kompresi Data yang Cerdas dan Efisien

 **"Kurangi ukuran, tanpa kehilangan makna."**

---

## 📌 Apa itu Huffman Coding?

**Huffman Coding** adalah algoritma kompresi data lossless yang menyandikan simbol berdasarkan frekuensi kemunculannya. Semakin sering suatu simbol muncul, semakin pendek representasi binernya.

---

## 🎯 Tujuan

Mengurangi ukuran data dengan cara menyandikan simbol-simbol menggunakan bit yang sepadan dengan frekuensinya—tanpa kehilangan informasi.

---

## 🧩 Konsep Dasar

1. Hitung frekuensi tiap simbol dalam data.
2. Bangun pohon Huffman:
   - Gabungkan dua simbol dengan frekuensi terendah menjadi simpul baru.
   - Ulangi hingga hanya satu simpul (akar pohon) tersisa.
3. Tetapkan kode:
   - Jalur ke kiri: `0`
   - Jalur ke kanan: `1`
   - Kode tiap simbol = jalur dari akar ke simpul tersebut

---

## 💡 Contoh Ilustratif

Misal string: `ABBCCCDDDDEEEEE`

| Simbol | Frekuensi |
|--------|-----------|
| A      | 1         |
| B      | 2         |
| C      | 3         |
| D      | 4         |
| E      | 5         |

Hasilnya: simbol `E` akan punya kode paling pendek, dan `A` paling panjang. Total panjang biner keseluruhan akan jauh lebih hemat dibanding penyandian tetap (fixed-length).

---

## ⚙️ Keunggulan

- ✅ Kompresi tanpa kehilangan data (lossless)
- ✅ Cocok untuk data dengan pola kemunculan berulang
- ✅ Digunakan dalam berbagai format kompresi modern (ZIP, JPEG, MP3)

---

## ⏱️ Kompleksitas

- **O(n log n)** untuk membangun pohon Huffman (dengan `n` simbol unik)

---

## 📦 Digunakan Dalam

- 🎧 Kompresi audio (MP3)
- 🖼️ Kompresi gambar (JPEG, PNG)
- 📄 Format arsip (ZIP, GZIP)

---


### 👑 N-Queens Problem – Algoritma Backtracking dalam Penempatan Optimal

**"Satu ratu per baris, satu langkah ke solusi."**

---

## 📌 Apa itu N-Queens Problem?

**N-Queens Problem** adalah tantangan algoritmik untuk menempatkan **N buah ratu** pada papan catur berukuran **N × N** sehingga **tidak ada ratu yang saling menyerang**—baik secara **vertikal, horizontal, maupun diagonal**.

---

## 🎯 Tujuan Utama

- Menempatkan tepat **N ratu di papan N × N**
- Setiap ratu harus berada pada posisi yang **aman**
- Tidak boleh ada dua ratu pada baris, kolom, atau diagonal yang sama

---

## 🧠 Mengapa Butuh Backtracking?

Masalah ini termasuk **Constraint Satisfaction Problem (CSP)**, di mana kita harus memilih kombinasi posisi yang memenuhi semua aturan. Pendekatan **backtracking** cocok karena:

- Bisa menyaring solusi tidak valid sejak awal
- Menghindari pencarian kombinasi brute force
- Lebih efisien dan sistematis

---

## 🧩 Langkah-Langkah Penyelesaian

1. Mulai dari baris pertama
2. Periksa posisi aman di kolom-kolom
3. Jika aman → tempatkan ratu
4. Lanjut ke baris berikutnya
5. Jika tidak ada posisi aman → kembali (backtrack) ke langkah sebelumnya
6. Ulangi hingga semua ratu ditempatkan

---

## 🧩 Langkah-Langkah Penyelesaian

1. Mulai dari baris pertama
2. Periksa posisi aman di kolom-kolom
3. Jika aman → tempatkan ratu
4. Lanjut ke baris berikutnya
5. Jika tidak ada posisi aman → kembali (backtrack) ke langkah sebelumnya
6. Ulangi hingga semua ratu ditempatkan

---

## ♟️ Contoh Kasus: N = 4

## 🧩 Langkah-Langkah Penyelesaian

1. Mulai dari baris pertama
2. Periksa posisi aman di kolom-kolom
3. Jika aman → tempatkan ratu
4. Lanjut ke baris berikutnya
5. Jika tidak ada posisi aman → kembali (backtrack) ke langkah sebelumnya
6. Ulangi hingga semua ratu ditempatkan

---

### 🧮 Subset Sum Problem – Mencari Kombinasi Angka yang Tepat

> *"Bukan soal berapa banyak yang kamu punya, tapi kombinasi mana yang tepat."*

---

## 📌 Apa itu Subset Sum Problem?

**Subset Sum** adalah salah satu permasalahan klasik dalam ilmu komputer, di mana kita diberi sebuah himpunan bilangan bulat dan diminta mencari apakah ada **subset (subhimpunan)** yang jumlah total elemennya **sama dengan nilai target** tertentu.

---

## 🧠 Karakter Masalah

- Termasuk ke dalam kategori **NP-Complete**  
  Artinya, masalah ini sulit diselesaikan secara efisien untuk semua kasus, tetapi **solusinya dapat diverifikasi dengan cepat** jika ditemukan.
- Digunakan dalam bidang **kriptografi, optimasi, dan teori kompleksitas**

---

## 🧩 Contoh Masalah

## text
- S = [3, 34, 4, 12, 5, 2]
- Target = 9 → ✅ Ya (karena 4 + 5 = 9)

Target = 30 → ❌ Tidak ada kombinasi yang cocok

---

### 🐭 Rat in a Maze – Menemukan Jalan dengan Backtracking

> *"Kadang hidup itu seperti labirin, dan kita cuma butuh satu jalan keluar."*

---

## 📌 Apa itu Rat in a Maze?

**Rat in a Maze** adalah masalah klasik dalam dunia algoritma, khususnya dalam topik **rekursi dan backtracking**. Seekor tikus harus mencari jalan dari titik awal ke titik akhir dalam sebuah labirin berbentuk matriks, hanya dengan mengikuti jalur yang dapat dilewati (biasanya ditandai dengan angka 1).

---

## 🎯 Tujuan

- Mencari semua atau salah satu jalur dari **titik awal (0,0)** ke **tujuan (N-1,N-1)** pada matriks NxN.
- Tikus hanya bisa bergerak ke arah **kanan (R)**, **kiri (L)**, **atas (U)**, atau **bawah (D)**, dan hanya melalui sel bernilai 1.

---

## 🧠 Mengapa Backtracking?

Algoritma ini menggunakan **pendekatan backtracking**, yaitu:

1. Coba langkah berikutnya yang mungkin.
2. Jika jalan buntu, **kembali (backtrack)** ke titik sebelumnya.
3. Ulangi hingga semua kemungkinan dicoba atau tujuan tercapai.

Metode ini efisien dalam eksplorasi jalur dan banyak digunakan dalam:

- Pemecahan puzzle (misalnya Sudoku)
- Sistem navigasi (GPS)
- Game development (AI pathfinding)

---

## 🗺️ Langkah Penyelesaian

1. Mulai dari posisi awal (0, 0).
2. Periksa apakah posisi saat ini valid (tidak keluar batas, bukan dinding, belum dikunjungi).
3. Tandai posisi sekarang sebagai bagian dari jalur.
4. Coba bergerak ke arah yang memungkinkan: bawah, kanan, atas, kiri.
5. Jika tidak ada jalur valid → backtrack ke posisi sebelumnya.
6. Ulangi hingga mencapai tujuan atau semua kemungkinan habis.

---

## 📋 Contoh Labirin

## text
1 0 0 0
1 1 0 0
0 1 1 0
0 1 1 1

---

### 🌐 Breadth-First Search (BFS) – Menjelajahi Graf Secara Bertahap

> **"Jelajahi dunia, satu level dalam satu waktu."**

---

## 📌 Apa itu Breadth-First Search?

**BFS (Breadth-First Search)** adalah algoritma pencarian pada graf atau pohon yang bekerja dengan cara **menelusuri simpul demi simpul secara melebar**—yakni dari level terdekat terlebih dahulu, lalu ke level yang lebih jauh.

BFS menggunakan struktur **antrian (queue)** untuk menentukan urutan simpul yang akan dijelajahi berikutnya.

---

## 🎯 Tujuan BFS

- Menjelajahi seluruh simpul yang dapat dicapai
- Menemukan **jalur terpendek** pada graf tak berbobot
- Deteksi **komponen terhubung**
- Digunakan dalam pencarian rute, AI game, sistem navigasi, dan algoritma lanjutan

---

## 🧠 Cara Kerja BFS (Langkah-langkah)

1. **Inisialisasi**:
   - Masukkan simpul awal ke dalam queue
   - Tandai simpul tersebut sebagai *sudah dikunjungi*
2. **Penelusuran**:
   - Selama queue tidak kosong:
     - Ambil simpul dari depan queue
     - Proses simpul
     - Masukkan semua tetangga yang belum dikunjungi ke dalam queue
3. **Selesai**:
   - Ulangi hingga semua simpul telah dikunjungi

---

## 🕸️ Ilustrasi Level

Urutan hasil BFS dari simpul A: `A → B → C → D → E → F`

---

## ⚙️ Kompleksitas BFS

- **Waktu**: `O(V + E)`
  - V = jumlah simpul (vertices)
  - E = jumlah sisi (edges)
- **Ruang**: `O(V)`
  - Untuk menyimpan queue dan daftar kunjungan

---

## 📦 Aplikasi BFS di Dunia Nyata

- 🔍 Pencarian jalur di peta atau jaringan
- 🤖 AI Game (menemukan rute terdekat)
- 🔗 Rekomendasi teman di media sosial (Facebook, Instagram)
- 📅 Penjadwalan tugas atau event

---

## 📝 Kesimpulan

BFS adalah algoritma dasar namun sangat penting dalam eksplorasi graf. Dengan sifatnya yang menjelajah per level, BFS cocok untuk menemukan **jalur terpendek**, menjelajahi semua koneksi, dan membentuk dasar dari berbagai algoritma lanjutan dalam dunia komputasi.

---

### *🌿Depth First Search (DFS)*
## 📖 Deskripsi Umum
Proyek ini merupakan implementasi dari algoritma Depth First Search (DFS) yang bertujuan untuk menjelajahi graf guna mencari simpul tertentu. DFS sangat berguna dalam banyak aplikasi seperti pemecahan maze, deteksi siklus pada graf, penyelesaian puzzle, dan sebagainya.

Proyek ini dibuat sebagai bagian dari tugas mata kuliah Algoritma dan Struktur Data, disusun oleh Kelompok 8.

## 🔎 Apa Itu DFS?
Depth First Search (DFS) adalah metode eksplorasi graf yang menjelajahi satu cabang hingga sejauh mungkin sebelum kembali dan menjelajahi cabang lainnya. DFS menggunakan pendekatan rekursif atau stack dalam implementasinya.

Karakteristik utama:
- Eksplorasi secara menyeluruh ke kedalaman graf.
- Dapat digunakan untuk pencarian jalur atau penelusuran seluruh simpul.
- Kurang efisien dibanding BFS jika solusi terletak dekat node awal.

## Cara Kerja DFS
Langkah-langkah utama dalam algoritma DFS:
- Mulai dari simpul awal.
- Tandai simpul sebagai telah dikunjungi.
- Telusuri simpul tetangga yang belum dikunjungi.
- Lanjutkan proses sampai tidak ada simpul baru yang bisa dikunjungi.
- Kembali (backtrack) dan telusuri jalur lainnya.

## Visualisasi Graf
**Graf yang digunakan dalam studi kasus:**
    A
   / \
  B   C
 /     \
D       E
Representasi graf dalam bentuk adjacency list:
graph = {
    'A': ['B', 'C'],
    'B': ['D'],
    'C': ['E'],
    'D': [],
    'E': []
}

# Definisi graf
graph = {
    'A': ['B', 'C'],
    'B': ['D'],
    'C': ['E'],
    'D': [],
    'E': []
}

# Set untuk menyimpan simpul yang sudah dikunjungi
visited = set()

# Fungsi rekursif DFS
def dfs(visited, graph, node):
    if node not in visited:
        print(node, end=" ")
        visited.add(node)
        for neighbour in graph[node]:
            dfs(visited, graph, neighbour)

# Menjalankan DFS dari simpul 'A'
print("Hasil Penelusuran DFS:")
dfs(visited, graph, 'A')
Hasil Penelusuran DFS:
A B D C E
Artinya, simpul dikunjungi secara mendalam terlebih dahulu: mulai dari A, menjelajah ke B, lalu ke D. Setelah itu, kembali ke A untuk mengunjungi C dan akhirnya ke E.

📈 Analisis dan Kesimpulan
Kelebihan:
- Implementasi sederhana dan efisien untuk graf kecil.
- Menemukan solusi lebih dalam secara cepat.
- Tidak membutuhkan banyak memori seperti BFS.

Kekurangan:
- Tidak menjamin menemukan jalur terpendek.
- Bisa terjebak dalam loop jika tidak ada pengecekan simpul yang telah dikunjungi.
- Kurang optimal untuk graf sangat besar dan kompleks.

## Kesimpulan:
Algoritma DFS merupakan pilihan yang tepat untuk penelusuran mendalam dan cocok digunakan dalam berbagai konteks seperti pemrosesan graf, pencarian solusi, dan deteksi siklus.

---

### *🎯 Kahn's Algorithm: Topological Sorting pada Graf Berarah*
## Apa itu Kahn's Algorithm?
Kahn's Algorithm adalah algoritma yang digunakan untuk melakukan topological sort pada graf berarah tanpa siklus (Directed Acyclic Graph atau DAG).

iperkenalkan oleh Arthur B. Kahn pada tahun 1962, algoritma ini membantu menyusun simpul dalam urutan yang logis.
👉 Jika ada edge dari simpul U ➝ V, maka U harus muncul sebelum V.

## Kegunaan Kahn’s Algorithm
Digunakan dalam berbagai bidang penting, seperti:
- Penjadwalan tugas (Task Scheduling)
- Kompilasi kode program (Compiler)
- Sistem build otomatis (Build Systems)
- Manajemen dependensi antar modul

## Konsep Utama dalam Kahn's Algorithm
1. DAG (Directed Acyclic Graph)
Graf berarah tanpa siklus
Contoh: Struktur organisasi, alur kerja proyek
2. Acyclic (Tanpa Siklus)
Tidak boleh ada jalur melingkar
Jika ada siklus → tidak bisa dilakukan topological sort
3. In-Degree
Jumlah edge yang masuk ke node
Node dengan in-degree = 0 bisa diproses lebih dulu
4. Topological Sort
Urutan simpul berdasarkan ketergantungan

Ciri-ciri:
- Hanya bisa untuk DAG
- Bisa ada banyak urutan yang sah
- Kompleksitas waktu: O(V + E)

## Langkah-Langkah Kahn’s Algorithm
- Hitung in-degree tiap simpul
- Masukkan semua simpul dengan in-degree = 0 ke queue

Selama queue tidak kosong:
- Ambil node dari queue
- Tambahkan ke hasil topological sort

Untuk tiap tetangganya:
- Kurangi in-degree
- Jika in-degree = 0 Masukkan ke queue
- ika semua node selesai diproses, berarti graf valid
- Jika tidak → terdapat siklus

## Contoh Soal
Graf:
1 → 2  
2 → 3  
1 → 4  
2 → 4  

Hitung In-degree:
Node    In-degree
1	      0
2	      1
3	      1
4	      2

Queue awal: [1]
Proses:
- Ambil 1 → hasil: [1]
2 jadi 0 → masuk queue
4 jadi 1
- Ambil 2 → hasil: [1, 2]
3 jadi 0 → masuk queue
4 jadi 0 → masuk queue
- Ambil 3 → [1, 2, 3]
- Ambil 4 → [1, 2, 3, 4]
- Hasil akhir: [1, 2, 3, 4]

Simulasi Kahn’s Algorithm:
- Dimulai dari node yang in-degree = 0
- Kurangi in-degree dari tetangga
- Jika in-degree jadi 0 → node bebas → bisa diproses
- Jika proses tidak bisa selesai → ada siklus

## Kesimpulan
Kahn's Algorithm berguna untuk menyusun urutan tugas berdasarkan dependensi
- Diterapkan dalam banyak sistem teknologi modern
- Dapat mendeteksi keberadaan siklus
- Waktu efisien: O(V + E)
- Tidak bisa digunakan untuk graf yang mengandung siklus

### *🧭 Dijkstra's Algorithm: Menemukan Jalur Terpendek dalam Graf*
## Pengertian Dijkstra's Algorithm
Dijkstra's Algorithm ditemukan oleh ilmuwan komputer asal Belanda, Edsger Dijkstra, dan pertama kali dipublikasikan pada tahun 1959 📜.
Algoritma ini digunakan untuk menemukan jalur terpendek dalam graf berarah dengan bobot sisi bernilai positif atau nol (≥ 0).

Dijkstra’s termasuk dalam kategori Greedy Algorithm (Algoritma Rakus), karena selalu memilih solusi lokal terbaik di setiap langkah untuk mencapai hasil global yang optimal.

## Tujuan Dijkstra's Algorithm
Tujuan utama algoritma ini adalah untuk menentukan jalur terpendek dari satu simpul awal ke simpul lainnya dalam graf berbobot positif.

## Contohnya:
Menentukan rute tercepat, termurah, atau paling efisien dari titik A ke titik B.

## Kegunaan Dijkstra's Algorithm dalam Kehidupan Nyata
Dijkstra’s Algorithm banyak digunakan dalam dunia nyata, di antaranya:
- Navigasi & Pemetaan Digital
Digunakan oleh aplikasi seperti Google Maps, Waze, GPS untuk mencari rute tercepat dengan mempertimbangkan jarak & waktu tempuh 🚗🛣️.
- Jaringan Komputer & Telekomunikasi
Digunakan dalam protokol routing seperti OSPF untuk menentukan jalur transmisi data yang paling efisien.
- Game Development
Membantu karakter/game AI dalam memilih rute terbaik untuk bergerak menuju target secara logis dan cepat.
- Logistik & Transportasi
Digunakan untuk merancang rute distribusi barang agar lebih hemat waktu dan biaya.
- Kecerdasan Buatan (AI)
Digunakan dalam robotika untuk perencanaan rute dan navigasi cerdas, serta dalam sistem rekomendasi.

## Cara Kerja Dijkstra's Algorithm
Langkah-langkah kerja algoritma ini:
Inisialisasi: 
- Pilih simpul awal → beri nilai 0
- Simpul lain → nilai awal ∞ (tak terhingga)
- Periksa semua tetangga simpul aktif
- Hitung total jarak dari simpul awal ke simpul tetangga

Perbarui Jarak Minimum:
- Jika jalur baru lebih pendek → perbarui nilai jarak
- Tandai simpul sebagai "terkunci"
Artinya simpul telah selesai diproses dan tidak diperiksa lagi

Ulangi:
- Pindah ke simpul dengan jarak terkecil yang belum dikunci
- Ulangi proses sampai semua simpul selesai atau tujuan tercapai

📊 Langkah Menggunakan Metode Tabel
Untuk mempermudah perhitungan manual, bisa gunakan tabel:
Langkah	Keterangan
- Buat tabel	Baris = simpul, Kolom = jarak dari simpul awal
- Pilih simpul awal dan tujuan	Pastikan simpul terhubung
- Hitung jarak	Dari simpul awal ke simpul tetangga
- Pilih jarak terpendek	Tetapkan simpul baru sebagai pusat perhitungan
- Ulangi	Sampai semua simpul mendapat jarak minimum

## Kesimpulan
Dijkstra’s Algorithm adalah salah satu algoritma paling penting dalam ilmu komputer, khususnya untuk menemukan jalur terpendek dalam graf berbobot positif.

Dengan prinsip Greedy, algoritma ini:
- Menyusun langkah demi langkah menuju hasil optimal
- Efisien digunakan dalam berbagai sektor teknologi & kehidupan nyata
- Menjamin jalur yang paling singkat dan logis antara dua titik

🚦 Tanpa Dijkstra, mungkin kita masih nyasar di jalan 😅!

