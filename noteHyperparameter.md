### **1. Perbedaan Parameter vs. Hiperparameter**
* **Parameter (*Model Parameters*)**: Nilai internal model yang dipelajari dan diperbarui secara otomatis dari data latih selama proses *training* menggunakan algoritma optimasi (seperti *gradient descent*). Contoh parameter adalah **bobot (*weights*)** dan **bias** pada node jaringan.
* **Hiperparameter (*Hyperparameters*)**: Pengaturan atau konfigurasi yang ditentukan oleh pengguna sebelum atau selama proses *training* dimulai. Hiperparameter tidak dipelajari langsung dari data, melainkan mengontrol alur pelatihan, arsitektur model, dan teknik regularisasi. Contohnya meliputi *learning rate*, *batch size*, jumlah *layer*, jumlah neuron, *dropout rate*, jenis *optimizer*, dan jumlah *epoch*.
* **Pentingnya Pemilihan Hiperparameter**:
  * Mengontrol kecepatan serta stabilitas konvergensi saat latihan.
  * Memengaruhi akurasi akhir dan kemampuan generalisasi pada data baru.
  * Membantu mencegah masalah *underfitting*, *overfitting*, maupun pelatihan yang tidak stabil.
  * Menentukan penggunaan sumber daya komputasi (waktu pelatihan dan memori).

---

### **2. Alur Pelatihan & Konsep Optimasi**
Proses pelatihan jaringan syaraf tiruan berjalan melalui empat tahapan utama yang diulang secara iteratif:
1. **Forward Pass**: Model menerima data masukan \\(x\\) dan menghasilkan prediksi \\(\hat{y}\\) berdasarkan parameter \\(\theta\\) saat itu.
2. **Kalkulasi Loss**: Mengukur seberapa besar tingkat kesalahan (*error*) antara prediksi \\(\hat{y}\\) dan label sebenarnya \\(y\\) menggunakan fungsi *loss* \\(L(\theta)\\) (misalnya *Cross-entropy loss* atau *Mean Squared Error*).
3. **Optimasi (Pembaruan Parameter)**: Menggunakan algoritma optimasi untuk memperbarui nilai parameter \\(\theta\\) agar nilai *loss* semakin mengecil dengan aturan umum pembaruan:
   \\[\theta_{t+1} = \theta_t - \eta \cdot \Delta \theta_t\\]
   di mana \\(\eta\\) adalah *learning rate* dan \\(\Delta \theta_t\\) adalah arah pembaruan gradien.
4. **Iterasi**: Menerapkan langkah 1–3 secara berulang untuk berbagai *mini-batch* dan *epoch* hingga model konvergen (nilai *loss* menjadi sangat kecil).

---

### **3. Algoritma Optimasi & *Learning Rate***
* **Tujuan Optimasi**: Menemukan kombinasi parameter \\(\theta^*\\) yang meminimalkan nilai fungsi *loss* (\\(\theta^* = \arg\min_\theta L(\theta)\\)).
* **Jenis Algoritma Optimasi**:
  1. **Gradient Descent (GD)**: Menghitung gradien berdasarkan keseluruhan dataset latih.
  2. **Stochastic Gradient Descent (SGD)**: Menggunakan gradien yang dihitung dari *mini-batch* data latih (estimasi gradien yang lebih bervariasi/*noisy*).
  3. **SGD dengan Momentum**: Memanfaatkan pembaruan masa lalu untuk mempercepat laju pembelajaran dan mengurangi osilasi.
  4. **Adam (*Adaptive Moment Estimation*)**: Menggunakan *learning rate* adaptif berbasis estimasi momen pertama dan kedua dari gradien; sangat luas digunakan dalam *deep learning*.
* ***Learning Rate* (\\(\eta\\))**: Hiperparameter yang menentukan seberapa besar langkah pembaruan parameter pada setiap tahap.
  * **Terlalu Besar (misal 0.1)**: Pelatihan menjadi tidak stabil dan *loss* berosilasi tanpa mencapai titik minimum.
  * **Terlalu Kecil (misal 0.0001)**: Proses konvergensi berjalan sangat lambat.
  * **Ideal (misal 0.01)**: *Loss* menurun secara cepat, stabil, dan konvergen dengan baik.

---

### **4. Pengaturan Komputasi: *Batch Size* & *Epoch***
* ***Batch Size***: Jumlah sampel data latih yang diproses bersamaan sebelum model melakukan satu kali pembaruan parameter.
  * **Jumlah Pembaruan per Epoch**: Dihitung dengan rumus \\(N / \text{batch\_size}\\) (di mana \\(N\\) adalah total data latih).
  * **Ukuran Kecil (misal 1 – 16)**: Memerlukan memori lebih sedikit dan gradien lebih bervariasi (*noisy*) yang membantu keluar dari *sharp minima*, tetapi pelatihannya bisa kurang stabil.
  * **Ukuran Sedang (misal 32 – 64)**: Keseimbangan yang ideal antara stabilitas dan variasi gradien, paling umum diterapkan.
  * **Ukuran Besar (misal 128 – 256)**: Estimasi gradien lebih stabil dan pelatihan per *epoch* lebih cepat pada perangkat keras paralel (GPU/TPU), tetapi membutuhkan memori besar dan berisiko terjebak pada *sharp minima*.
* ***Epoch***: Satu putaran lengkap di mana model telah melihat seluruh sampel dalam dataset latih tepat satu kali. Selama satu *epoch*, data umumnya diacak (*shuffled*) dan model melakukan pembaruan parameter berkali-kali melalui *mini-batch*.

---

### **5. Teknik Regularisasi: *Dropout***
* **Pengertian**: Teknik regularisasi yang digunakan selama proses *training* dengan cara mematikan (*drop*/set ke nol) sebagian aktivasi neuron secara acak.
* **Tujuan**: Mencegah jaringan terlalu bergantung pada neuron tertentu saja sehingga mengurangi risiko *overfitting* dan menghasilkan fitur yang lebih tangguh (*robust*).
* ***Dropout Rate* (\\(p\\))**: Probabilitas sebuah neuron dimatikan (nilai umum: 0.2, 0.3, atau 0.5; nilai \\(p=0.5\\) berarti rata-rata 50% neuron dimatikan selama *training*).
* **Perbedaan *Train* vs. *Inference***:
  * **Saat *Training***: Neuron dimatikan secara acak sesuai nilai \\(p\\), dan neuron yang mati tidak berkontribusi pada *forward pass* maupun pembaruan gradien.
  * **Saat *Inference/Testing***: Seluruh neuron diaktifkan dan nilai aktivasinya disesuaikan (*scaled*) agar skala output tetap konsisten dengan saat *training*.
* **Efek & Pertimbangan**: Efektif menjaga *validation loss* tetap rendah bersamaan dengan *training loss*. Namun, jika nilai *dropout rate* terlalu tinggi, model dapat mengalami *underfitting* dan membutuhkan waktu konvergensi lebih lama.

---

### **6. Tabel Ringkasan Hiperparameter**

| Hiperparameter | Fungsi Pengaturan | Nilai Tipikal | Efek Jika Terlalu Sedikit / Kecil | Efek Jika Terlalu Banyak / Besar |
| :--- | :--- | :--- | :--- | :--- |
| ***Learning Rate*** | Ukuran langkah pembaruan parameter | 0.1, 0.01, 0.001 | Konvergensi sangat lambat | Pelatihan tidak stabil / osilasi |
| ***Batch Size*** | Jumlah sampel per satu kali pembaruan parameter | 16, 32, 64, 128 | Variasi gradien tinggi, update lebih sering | Butuh memori besar, risiko terjebak *sharp minima* |
| **Jumlah *Layer*** | Kedalaman arsitektur jaringan (*depth*) | 1, 2, 3, 5, ... | Risiko *underfitting* | Biaya komputasi tinggi, risiko *overfitting* |
| **Jumlah Neuron** | Kapasitas / lebar tiap *layer* (*width*) | 32, 64, 128, ... | Risiko *underfitting* | Biaya komputasi tinggi, risiko *overfitting* |
| ***Dropout Rate*** | Proporsi neuron yang dimatikan saat *training* | 0.2, 0.3, 0.5 | Risiko *overfitting* | Risiko *underfitting*, pelatihan lebih lambat |
| ***Jumlah Epoch*** | Jumlah putaran lengkap melalui seluruh dataset | 10, 50, 100, ... | Risiko *underfitting* | Berisiko mengalami *overfitting* |

---

