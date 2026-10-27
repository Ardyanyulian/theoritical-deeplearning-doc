### **Konsep Utama & Tren AI**
* **Artificial Intelligence (AI), Machine Learning (ML), dan Deep Learning (DL)**: Neural Network dan Deep Learning merupakan tren utama dalam bidang AI untuk menyelesaikan berbagai tugas komputasi kecerdasan buatan.
* **Alur Supervised Learning**: Proses klasifikasi umumnya membagi data menjadi **data training (data latih)** untuk membangun model dan **data testing (data uji)** untuk menguji kinerja model melalui metrik seperti akurasi, *precision*, *recall*, serta *F1-score*.

---

### **Definisi Artificial Neural Network (ANN)**
* **Pengertian**: ANN (Jaringan Syaraf Tiruan) adalah sistem komputasi yang terdiri dari elemen pemroses sederhana yang saling terhubung untuk memproses informasi secara dinamis terhadap masukan eksternal.
* **Inspirasi Biologis**: ANN terinspirasi oleh sistem syaraf otak manusia yang memiliki sekitar **86 miliar neuron** yang terhubung oleh **\\(10^{14}\\) hingga \\(10^{15}\\) sinapsis**.

---

### **Model Matematika Neuron**
* **Neuron (Node / Unit)**: Merupakan unit komputasi terkecil yang menerima masukan, memprosesnya, dan menghasilkan keluaran.
* **Bobot (*Weight* - \\(w\\))**: Setiap masukan diberi bobot yang menentukan kadar kepentingan (*importance*) dari data masukan tersebut.
* **Penjumlahan Berbobot (*Weighted Sum*) & Bias**: Neuron menghitung penjumlahan berbobot (*weighted sum*) dari seluruh masukan ditambah nilai **bias (\\(b\\))**, lalu meneruskannya ke **fungsi aktivasi** untuk menghasilkan nilai keluaran (\\(y\\)).

---

### **Arsitektur Feed Forward Neural Network (FFNN)**
Pada jenis jaringan ini, informasi diproses secara searah dari depan ke belakang (**Input Layer \\(\rightarrow\\) Hidden Layer \\(\rightarrow\\) Output Layer**):
* **Input Layer**: Tidak melakukan pemrosesan data, hanya meneruskan (*passing*) nilai masukan ke lapisan berikutnya.
* **Hidden Layer**: Lapisan tempat dilakukannya komputasi utama, yaitu kalkulasi penjumlahan berbobot dan penerapan fungsi aktivasi.
* **Output Layer**: Menerapkan fungsi aktivasi akhir untuk menghasilkan prediksi.
* **Koneksi & Bobot**: Keluaran dari suatu node menjadi masukan bagi node di lapisan berikutnya, di mana tiap koneksi memiliki nilai bobot masing-masing.
* **Variasi Bentuk**:
  * **Single Perceptron**: Bentuk jaringan syaraf paling dasar dengan satu lapisan tunggal.
  * **Multi Layer Perceptron (MLP)**: Memiliki beberapa lapisan terhubung (*Fully Connected Layer*).

---

### **Fungsi Aktivasi (*Activation Function*)**
Fungsi aktivasi adalah fungsi (umumnya **non-linear**) yang mentransformasikan hasil penjumlahan berbobot menjadi nilai keluaran node dan memengaruhi kinerja model secara keseluruhan.

1. **Fungsi Aktivasi pada Hidden Layer**:
   * **ReLU (*Rectified Linear Unit*)**: Menghasilkan nilai maksimum antara \\(z\\) dan \\(0\\) (\\(a = \max(0, z)\\)). Paling sering digunakan pada MLP dan CNN.
   * **Sigmoid (*Logistic*)**: Mengubah masukan menjadi nilai kurva terikat.
   * **Tanh (*Hyperbolic Tangent*)**: Mengubah masukan menggunakan fungsi hiperbolik.

2. **Fungsi Aktivasi pada Output Layer**:
   * **Linear**: Digunakan untuk permasalahan **Regresi** (*Regression*).
   * **Sigmoid**: Digunakan untuk permasalahan **Klasifikasi Biner** (*Binary Classification*) dan **Klasifikasi Multilabel** (*Multilabel Classification*).
   * **Softmax**: Menghasilkan nilai probabilitas antara 0 hingga 1 dan digunakan untuk **Klasifikasi Multikelas** (*Multiclass Classification*).

---

### **Proses Training & Pengenalan Deep Learning**
* **Proses Training**: Proses pelatihan komputer untuk menemukan kombinasi nilai **bobot (\\(w\\))** dan parameter lain secara otomatis agar keluaran model sesuai dengan target.
* **Deep Learning**: Disebut juga *Deep Neural Network*, yaitu arsitektur jaringan syaraf yang memiliki jumlah *hidden layer* sangat banyak.
* **Variasi Arsitektur Modern**: Perkembangan Neural Network mencakup berbagai arsitektur khusus seperti **Convolutional Neural Network (CNN)**, **Recurrent Neural Network (RNN - LSTM/GRU)**, **Residual Network (ResNet)**, **Generative Adversarial Network (GAN)**, **Graph Neural Network**, hingga **Transformer**.


---

### **1. Perbedaan Arsitektur Utama**
* **Shallow Neural Network (SNN)**: Memiliki arsitektur yang sederhana dengan **hanya satu *hidden layer***.
* **Deep Neural Network (DNN)**: Memiliki arsitektur yang lebih kompleks dengan **jumlah *hidden layer* yang banyak** (dapat terdiri dari beberapa, puluhan, ratusan, ribuan, bahkan jutaan *layer* tergantung kasus). Dengan banyaknya *hidden layer*, DNN mampu mempelajari **fitur-fitur tersembunyi (*hidden features*)** secara hirarkis dari data.

---

### **2. Kompleksitas & Jumlah Parameter**
* **Proses *Training***: Merupakan proses untuk menemukan kombinasi **bobot (*weight/parameter*)** yang tepat pada setiap koneksi antar-node agar menghasilkan nilai **keluaran (*output*) dengan nilai *loss* terkecil**.
* **Jumlah Parameter**: Jumlah bobot yang harus dilatih sama dengan **jumlah garis koneksi antar-node** di dalam jaringan.
* **Dampak Penambahan *Layer***: Semakin banyak *layer* dan node, semakin banyak jumlah parameter yang harus di-*training*. Hal ini menyebabkan **waktu *training* menjadi lebih lama** dan **penggunaan memori menjadi lebih besar**.
* **SNN vs DNN**:
  * **Shallow NN**: Memiliki parameter yang relatif sedikit sehingga lebih mudah di-*training* serta **lebih murah dari segi waktu dan memori**.
  * **Deep NN**: Memiliki jumlah parameter yang sangat besar (bisa mencapai jutaan parameter), sehingga **lebih *costly*** (membutuhkan waktu komputasi dan kapasitas memori yang tinggi).

---

### **3. Kapasitas Pembelajaran (*Learning Capacity*)**
* **Shallow Neural Network**: Memiliki kapasitas belajar yang terbatas, sehingga hanya cocok untuk **kasus-kasus sederhana** (seperti klasifikasi linear atau *binary classification* yang kelasnya mudah dipisahkan secara langsung).
* **Deep Neural Network**: Memiliki kapasitas belajar yang sangat tinggi. Mampu memahami hirarki pola pada data yang rumit, sehingga cocok untuk menyelesaikan **masalah kompleks** seperti pengenalan gambar/video, pemrosesan bahasa alami (*Natural Language Processing*), dan pemrosesan *big data* secara *real-time*.

---

### **4. Risiko *Overfitting***
* **Pengertian *Overfitting***: Kondisi ketika model mempelajari data *training* terlalu detail (termasuk *noise* pada data), sehingga memiliki **kemampuan generalisasi yang buruk** pada data baru (*unseen data/testing data*). Ciri utamanya adalah **akurasi data *training* sangat tinggi, tetapi akurasi data *testing* rendah**.
* **Risiko pada Shallow NN**: Memiliki **risiko *overfitting* yang lebih rendah** karena jumlah parameternya sedikit dan memorinya terbatas untuk mengingat detail data *training*.
* **Risiko pada Deep NN**: Sangat **rentan mengalami *overfitting*** karena jumlah parameternya yang sangat banyak cenderung menghafal seluruh pola data latih.
* **Solusi Pencegahan pada DNN**: Untuk menghindari *overfitting* pada DNN, diperlukan teknik khusus seperti ***regularization***, ***dropout***, dan ***early stopping***.

---

### **5. Kebutuhan Data (*Data Requirement*)**
* **Shallow Neural Network**: Cenderung hanya membutuhkan **jumlah data yang kecil** untuk proses *training* yang efektif.
* **Deep Neural Network**: Membutuhkan **jumlah data yang sangat besar** agar pelatihan berjalan efektif. Jika data yang tersedia terbatas, penggunaan arsitektur *Deep Neural Network* tidak diperlukan.

---

### **6. Sumber Daya Komputasi (*Computational Resources*)**
* **CPU vs GPU**: *Training* Deep NN dengan dataset besar membutuhkan waktu sangat lama jika menggunakan **CPU**. Oleh karena itu, lebih disarankan menggunakan **GPU (*Graphics Processing Unit*)** karena mendukung **pemrosesan paralel (*parallel processing*)** yang jauh lebih cepat.
* **TPU (*Tensor Processing Unit*)**: Merupakan akselerator perangkat keras khusus yang dirancang oleh Google untuk mempercepat tugas *machine learning*, khususnya operasi **perkalian matriks**. TPU memberikan peningkatan kinerja dan efisiensi yang lebih tinggi dibandingkan CPU dan GPU tradisional.

---

### **7. Ringkasan Perbandingan: Shallow vs Deep NN**

| Parameter | Shallow Neural Network | Deep Neural Network |
| :--- | :--- | :--- |
| **Jumlah *Hidden Layer*** | Tepat 1 *Hidden Layer* | Banyak *Hidden Layer* (puluhan hingga jutaan) |
| **Jumlah Parameter/Bobot** | Sedikit | Sangat Banyak |
| **Kapasitas Belajar** | Rendah (Kasus sederhana/linear) | Tinggi (Kasus kompleks, hirarki pola) |
| **Risiko *Overfitting*** | Rendah | Tinggi (Butuh *Dropout/Regularization*) |
| **Kebutuhan Data** | Kecil | Sangat Besar |
| **Kebutuhan Hardware** | Cukup dengan CPU | Membutuhkan GPU / TPU |

---

### **8. Contoh Model**
* **Shallow Neural Network**: *Single Layer Perceptron*.
* **Deep Neural Network**: *Multi Layer Perceptron* (MLP dengan banyak *layer*), *Convolutional Neural Networks* (CNN), *Recurrent Neural Networks* (RNN), dan lain-lain.

---

