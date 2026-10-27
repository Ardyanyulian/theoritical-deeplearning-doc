--

### **1. Pengertian & Kegunaan CNN**
* **Definisi**: *Convolutional Neural Networks* (CNN atau ConvNet) adalah algoritma *Deep Learning* yang menggabungkan struktur *Artificial Neural Network* (ANN) dengan operasi konvolusi (**CNN = ANN + konvolusi**).
* **Penggunaan Utama**: Dirancang secara khusus untuk memproses dan menganalisis data berbentuk citra atau gambar.
* **Tugas (*Tasks*) Utama**:
  * **Klasifikasi Gambar (*Image Classification*)**: Mengelompokkan gambar ke dalam kategori/kelas tertentu.
  * **Pengenalan Objek (*Object Detection*)**: Mendeteksi serta menentukan letak objek spesifik di dalam gambar.

---

### **2. Alur Kerja Utama CNN**
Proses pengolahan citra pada CNN dibagi menjadi dua tahapan besar, yaitu **Feature Detection / Feature Extraction** dan **Classification**:

1. **Memecah Gambar (*Tiling*)**: Gambar input dipotong menjadi bagian-bagian kecil yang saling tumpang tindih (*overlapping*) menggunakan proses konvolusi.
2. **Pemrosesan *Small Neural Network***: Setiap potongan gambar kecil diproses melalui *small neural network* yang menggunakan bobot terbagi (*shared weights*).
3. **Pembentukan Feature Map**: Hasil pemrosesan dari seluruh potongan gambar disimpan ke dalam matriks baru yang dinamakan **Feature Map**.
4. **Downsampling (*Pooling*)**: Memperkecil ukuran *feature map* untuk mereduksi dimensi data.
5. **Klasifikasi (*Fully Connected Layer*)**: Fitur yang telah diekstrak dan dipampatkan dihubungkan ke *Fully Connected Neural Network* untuk menghasilkan nilai prediksi kelas.

---

### **3. Komponen & Parameter Utama pada CNN**

1. **Convolutional Layer (Lapisan Konvolusi)**
   Lapisan utama yang bertugas mengekstrak fitur-fitur visual dari gambar. Pada pustaka seperti TensorFlow (`tf.keras.layers.Conv2D`), terdapat beberapa parameter penting:
   * **`filters`**: Jumlah filter/kernel yang digunakan pada *convolution layer* untuk menangkap berbagai karakteristik gambar.
   * **`kernel_size`**: Ukuran matriks filter (\\(n \times n\\)), contohnya \\(3 \times 3\\) atau \\(5 \times 5\\).
   * **`stride`**: Jarak pergeseran posisi filter saat menyapu gambar (jika `stride = 1`, filter bergeser 1 piksel pada setiap langkah).
   * **`padding`**: Pengaturan batas pinggir gambar saat proses konvolusi:
     * **`valid`**: Tanpa penambahan piksel pada batas gambar, sehingga ukuran *output feature map* mengecil.
     * **`same`**: Menambahkan piksel di sekeliling gambar agar ukuran *output feature map* tetap sama dengan ukuran gambar input.

2. **Fungsi Aktivasi (ReLU)**
   Biasanya diterapkan langsung setelah operasi konvolusi (*Convolution + ReLU*) untuk memberikan sifat non-linear pada *feature map*.

3. **Pooling Layer (Lapisan Pemampatan)**
   Digunakan untuk mereduksi dimensi *feature map* (*downsampling*) sehingga mempercepat komputasi dan menghemat memori. Dua jenis pooling yang umum adalah:
   * **Max Pooling**: Mengambil nilai tertinggi/maksimal dari setiap area filter (misalnya filter \\(2 \times 2\\) dengan `stride = 2`).
   * **Average Pooling**: Mengambil nilai rata-rata piksel dari area filter.

4. **Flatten Layer & Fully Connected Layer (FC / Dense Layer)**
   * **Flatten Layer**: Meratakan matriks multidimensi dari *feature map* menjadi vektor 1 dimensi.
   * **Fully Connected Layer**: Menghubungkan seluruh neuron dari *flatten layer* ke lapisan padat (*Dense Layer*) untuk memproses fitur akhir.
   * **Output Layer**: Menggunakan fungsi aktivasi akhir seperti **Softmax** (untuk klasifikasi multikelas) atau **Sigmoid** (untuk klasifikasi biner) guna menghasilkan probabilitas prediksi.

---

