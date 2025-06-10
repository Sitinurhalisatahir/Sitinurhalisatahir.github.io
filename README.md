# 🗂️ Activity Selection Problem (ASP)

**Solusi optimal untuk penjadwalan aktivitas tanpa konflik waktu menggunakan pendekatan _Greedy Algorithm_**

---

## 📌 Deskripsi

Activity Selection Problem (ASP) adalah masalah optimasi yang bertujuan untuk memilih sebanyak mungkin aktivitas dari sebuah daftar, dengan syarat **tidak ada aktivitas yang saling tumpang tindih**.

Masalah ini sering dijumpai dalam berbagai skenario nyata:
- 📅 Penjadwalan ruang kelas
- 💼 Jadwal wawancara kerja
- 🛠️ Pengelolaan mesin atau sumber daya

---

## 💡 Algoritma yang Digunakan

ASP diselesaikan menggunakan **Greedy Algorithm**, yakni strategi yang mengambil keputusan terbaik secara lokal pada setiap langkah untuk mencapai hasil global yang optimal.

### Kenapa Greedy?
- Memilih aktivitas yang selesai lebih awal memberi ruang lebih banyak untuk aktivitas lainnya.
- Efisien dan mudah diimplementasikan.

---

## 🛠️ Langkah Penyelesaian

1. **Urutkan aktivitas berdasarkan waktu selesai (meningkat).**
2. **Pilih aktivitas pertama** (yang selesai paling cepat).
3. Untuk setiap aktivitas berikutnya:
   - Pilih jika waktu mulai ≥ waktu selesai aktivitas terakhir yang dipilih.
4. Ulangi sampai akhir.

---

## 🧪 Contoh

| Aktivitas | Mulai | Selesai |
|-----------|-------|---------|
| A         | 1     | 4       |
| B         | 3     | 5       |
| C         | 0     | 6       |
| D         | 5     | 7       |
| E         | 8     | 9       |
| F         | 5     | 9       |

✔️ Hasil optimal: **A, D, E**  
📈 Total aktivitas terpilih: **3**

---

## 💻 Implementasi

Kode berikut adalah contoh implementasi ASP dalam bahasa C++:

```cpp
struct Activity {
    int start, finish;
};

bool compare(Activity a1, Activity a2) {
    return a1.finish < a2.finish;
}

void activitySelection(vector<Activity> &activities) {
    sort(activities.begin(), activities.end(), compare);

    cout << "Aktivitas terpilih:\n";
    int lastFinish = activities[0].finish;
    cout << "[Start: " << activities[0].start << ", Finish: " << activities[0].finish << "]\n";

    for (int i = 1; i < activities.size(); i++) {
        if (activities[i].start >= lastFinish) {
            cout << "[Start: " << activities[i].start << ", Finish: " << activities[i].finish << "]\n";
            lastFinish = activities[i].finish;
        }
    }
}

# 🎒 Fractional Knapsack – Strategi Greedy untuk Nilai Maksimal

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
