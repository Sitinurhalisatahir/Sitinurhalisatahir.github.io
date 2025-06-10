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

