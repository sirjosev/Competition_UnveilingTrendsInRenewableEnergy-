# Prediksi Tren Energi Terbarukan 🌍🔋

## Tujuan Proyek

Proyek ini bertujuan untuk membangun model machine learning yang kuat untuk memprediksi produksi energi terbarukan (dalam GWh) di berbagai negara. Dengan menggunakan dataset yang kaya akan indikator seperti PDB, populasi, emisi karbon, dan metrik kebijakan, model ini diharapkan dapat membantu dalam pengambilan keputusan investasi yang lebih cerdas, perumusan kebijakan yang berwawasan ke depan, dan percepatan transisi global menuju energi bersih.

Proyek ini merupakan solusi untuk tantangan kompetisi "Unveiling Trends in Renewable Energy" yang diselenggarakan oleh DataCamp, di mana tujuannya adalah untuk melatih model pada data historis dan menghasilkan prediksi untuk set data pengujian.

## Struktur Repositori

Berikut adalah penjelasan mengenai struktur direktori dan file-file penting dalam repositori ini:

```
/
├── 📄 Competition_Unveiling_trends_in_renewable_energy.ipynb
│   └── Notebook utama yang berisi seluruh alur kerja proyek, mulai dari analisis data eksplorasi, rekayasa fitur, pelatihan model, hingga evaluasi dan pembuatan prediksi.
│
├── 📁 data/
│   ├── 📊 Training_set_augmented.csv
│   │   └── Dataset yang digunakan untuk melatih model machine learning. Berisi fitur-fitur dan variabel target (`Production (GWh)`).
│   └── 📊 Public_Test_Set.csv
│       └── Dataset yang digunakan untuk pengujian. Berisi fitur yang sama dengan data training, tetapi tanpa variabel target.
│
├── 📄 notebook.ipynb
│   └── Notebook tambahan atau versi lain dari analisis.
│
└── 📖 README.md
    └── Dokumentasi lengkap proyek ini yang sedang Anda baca.
```

## Stack Teknologi

Proyek ini dibangun menggunakan bahasa pemrograman Python dan beberapa pustaka utama untuk analisis data, machine learning, dan visualisasi.

*   **Analisis & Manipulasi Data:**
    *   `pandas`: Untuk memuat, membersihkan, dan memanipulasi data tabular.
    *   `numpy`: Untuk operasi numerik yang efisien.
*   **Machine Learning:**
    *   `scikit-learn`: Untuk pra-pemrosesan data (scaling, encoding) dan validasi model.
    *   `lightgbm`: Sebagai model utama untuk prediksi (Gradient Boosting Machine).
*   **Visualisasi & Interpretasi:**
    *   `matplotlib` & `seaborn`: Untuk membuat visualisasi data statis.
    *   `geopandas`: Untuk analisis dan visualisasi data geospasial.
    *   `shap`: Untuk menginterpretasikan dan menjelaskan hasil prediksi model.
*   **Lingkungan Kerja:**
    *   `Jupyter Notebook`: Untuk pengembangan interaktif dan dokumentasi alur kerja.

## Alur Kerja Program

Proyek ini mengikuti alur kerja yang sistematis untuk memastikan hasil yang andal dan dapat direproduksi. Berikut adalah tahapan-tahapan utamanya:

1.  **Inisialisasi dan Pemuatan Data**
    *   Mengimpor semua pustaka yang dibutuhkan.
    *   Memuat dataset training (`Training_set_augmented.csv`) dan testing (`Public_Test_Set.csv`) menggunakan `pandas`.
    *   Melakukan validasi dasar untuk memastikan data dimuat dengan benar.

2.  **Analisis Data Eksplorasi (EDA)**
    *   Melakukan inspeksi data untuk memahami struktur, tipe data, dan distribusi variabel.
    *   Menganalisis nilai yang hilang (missing values) dan statistik deskriptif dari setiap fitur.
    *   Menganalisis distribusi variabel target (`Production (GWh)`) dan menerapkan transformasi logaritmik untuk menormalkan distribusinya.

3.  **Rekayasa Fitur (Feature Engineering)**
    *   Membuat fitur-fitur baru yang relevan untuk meningkatkan kekuatan prediksi model. Beberapa fitur yang dibuat antara lain:
        *   Fitur temporal (`Decade`, `Post_Paris_Agreement`).
        *   Metrik efisiensi ekonomi (`GDP_per_Capita`, `CO2_per_GDP`).
        *   Indeks momentum kebijakan (`Policy_Momentum`).
        *   Indeks komposit potensi energi terbarukan (`Renewable_Potential`).

4.  **Pra-pemrosesan Data**
    *   Memisahkan fitur (X) dan target (y).
    *   Mengidentifikasi fitur numerik dan kategorikal.
    *   Menerapkan `StandardScaler` pada fitur numerik untuk menyeragamkan skala.
    *   Menerapkan `OneHotEncoder` pada fitur kategorikal untuk mengubahnya menjadi format numerik.

5.  **Strategi Validasi Model**
    *   Menggunakan `TimeSeriesSplit` untuk membuat skema validasi silang (cross-validation) yang sesuai untuk data deret waktu. Hal ini penting untuk mencegah kebocoran data (data leakage) dari masa depan ke masa lalu.

6.  **Pelatihan Model**
    *   Melatih model **LightGBM (Light Gradient Boosting Machine)**, yang dikenal karena kecepatan dan efisiensinya.
    *   Menggunakan mekanisme *early stopping* untuk menemukan jumlah iterasi optimal dan mencegah *overfitting*.

7.  **Interpretasi Model**
    *   Menggunakan pustaka `SHAP` (SHapley Additive exPlanations) untuk memahami bagaimana model membuat prediksi.
    *   Membuat visualisasi seperti *summary plot* dan *dependence plot* untuk mengidentifikasi fitur-fitur yang paling berpengaruh.

8.  **Pembuatan Prediksi dan Submisi**
    *   Menggunakan model yang telah dilatih untuk menghasilkan prediksi pada `Public_Test_Set.csv`.
    *   Menyimpan hasil prediksi dalam format CSV yang sesuai dengan persyaratan kompetisi.

## Cara Penggunaan

Untuk menjalankan proyek ini di lingkungan lokal Anda, ikuti langkah-langkah berikut:

1.  **Clone Repositori**
    ```bash
    git clone https://github.com/sirjosev/Competition_UnveilingTrendsInRenewableEnergy-.git
    cd Competition_UnveilingTrendsInRenewableEnergy-
    ```

2.  **Buat Lingkungan Virtual (Direkomendasikan)**
    ```bash
    python -m venv venv
    source venv/bin/activate  # Di Windows, gunakan `venv\Scripts\activate`
    ```

3.  **Instal Dependensi**
    Pastikan Anda memiliki file `requirements.txt` yang berisi semua pustaka yang dibutuhkan.
    ```bash
    pip install -r requirements.txt
    ```

4.  **Jalankan Jupyter Notebook**
    Setelah semua dependensi terinstal, jalankan server Jupyter.
    ```bash
    jupyter notebook
    ```
    Buka file `Competition_Unveiling_trends_in_renewable_energy.ipynb` dari antarmuka Jupyter dan jalankan sel-selnya secara berurutan untuk mereproduksi seluruh alur kerja.

## Cara Deployment (Hipotetis)

Meskipun proyek ini disajikan dalam format notebook, artefak yang dihasilkan (seperti `model.pkl` dan `preprocessor.pkl` yang disimpan di bagian akhir notebook) dapat di-deploy untuk penggunaan di dunia nyata.

Salah satu pendekatan yang umum adalah dengan membuat sebuah API (Application Programming Interface) menggunakan framework seperti **Flask** atau **FastAPI**.

Berikut adalah alur kerja konseptualnya:

1.  **Simpan Artefak Model:** Jalankan notebook hingga sel terakhir untuk menghasilkan file `model.pkl` (model terlatih) dan `preprocessor.pkl` (pipeline pra-pemrosesan).

2.  **Buat Endpoint API:** Buat sebuah endpoint (misalnya, `/predict`) yang menerima data baru dalam format JSON.

3.  **Proses dan Prediksi:**
    *   Endpoint akan memuat `model.pkl` dan `preprocessor.pkl`.
    *   Data JSON yang masuk diubah menjadi DataFrame `pandas`.
    *   Pipeline pra-pemrosesan (`preprocessor.pkl`) diterapkan pada data baru.
    *   Model (`model.pkl`) digunakan untuk membuat prediksi pada data yang telah diproses.

4.  **Kirim Respon:** API akan mengembalikan hasil prediksi dalam format JSON.

Pendekatan ini memungkinkan model untuk diintegrasikan dengan aplikasi lain, dasbor, atau sistem backend untuk membuat prediksi secara *real-time*.

## Kontribusi

Kontribusi dari komunitas sangat kami hargai! Jika Anda ingin berkontribusi pada proyek ini, silakan ikuti langkah-langkah berikut:

1.  **Fork Repositori:** Buat *fork* dari repositori ini ke akun GitHub Anda.
2.  **Buat Branch Baru:** Buat *branch* baru untuk fitur atau perbaikan yang Anda kerjakan (`git checkout -b nama-fitur-anda`).
3.  **Lakukan Perubahan:** Lakukan perubahan atau penambahan kode Anda.
4.  **Commit Perubahan:** Lakukan *commit* terhadap perubahan Anda dengan pesan yang jelas (`git commit -m 'Menambahkan fitur X'`).
5.  **Push ke Branch:** *Push* perubahan Anda ke *branch* di repositori *fork* Anda (`git push origin nama-fitur-anda`).
6.  **Buat Pull Request:** Buka *Pull Request* dari *branch* Anda ke *branch* `master` dari repositori asli.

Beberapa ide untuk kontribusi:
*   Mencoba model machine learning lain (misalnya, XGBoost, CatBoost).
*   Menambahkan lebih banyak fitur melalui rekayasa fitur.
*   Mengoptimalkan hyperparameter model lebih lanjut.
*   Membuat dasbor interaktif untuk visualisasi hasil.
