# Analisis Komparatif Performa Kernel SGEMM GPU: Baseline OLS vs Robust Huber Regressor

Proyek ini bertujuan untuk mengevaluasi performa model regresi dalam memprediksi waktu eksekusi kernel GPU. Fokus utama penelitian adalah menguji ketahanan (*robustness*) model melalui mekanisme **Stress Test** dengan menyuntikkan *outlier* buatan ke dalam dataset. 

## 📋 Ringkasan Proyek

Penelitian ini menggunakan dataset **SGEMM GPU kernel performance** (241.600 baris) untuk memodelkan hubungan antara parameter konfigurasi kernel (MWG, NWG, dll.) terhadap waktu eksekusi (Run1-Run4). Kami membandingkan pendekatan regresi klasik (OLS) dengan pendekatan tangguh (*Robust*) yaitu Huber Regressor. 

## 🚀 Keterbaruan (Novelty)

Berbeda dengan implementasi regresi standar dari tools AI biasa, repositori ini menyertakan modifikasi manual berupa: 

1. **Clean Code & Modular Config:** Implementasi objek `CONFIG` sebagai pusat kendali parameter eksperimen. 
2. **Mekanisme Stress Test Manual:** Algoritma khusus untuk menyuntikkan 5% *outlier* (10x lipat nilai asli) guna mensimulasikan kegagalan data sensor. 
3. **Data Persistence:** Fitur ekspor otomatis hasil evaluasi ke dalam file CSV untuk dokumentasi riset yang *reproducible*. 
4. **Visualisasi Terintegrasi:** Pembuatan grafik perbandingan MAPE menggunakan Seaborn untuk memudahkan interpretasi data secara visual. 
5. **Optimasi Memori:** Penggunaan tipe data `float32` untuk memastikan efisiensi pemrosesan dataset skala besar pada lingkungan komputasi terbatas. 



## 🛠️ Metodologi Preprocessing

* **Target Aggregation:** Menggabungkan empat kolom *runtime* (Run1-Run4) menjadi satu nilai rata-rata untuk mengurangi *experimental noise*. 
* **Standardization:** Menggunakan `StandardScaler` dalam sebuah *Pipeline* untuk menyamakan skala 14 fitur input, mencegah bias pada model regresi. 
* **Validation:** Implementasi **5-Fold Cross Validation** untuk menjamin stabilitas hasil evaluasi dan mencegah *data leakage*. 



## 📊 Hasil Eksperimen Singkat

Berdasarkan pengujian pada Bab III laporan kami:

* **Kondisi Normal:** OLS dan Huber menunjukkan performa yang kompetitif dengan $R^{2}$ mencapai ~0.40. 
* **Kondisi Stress Test:** Akurasi OLS menurun drastis dengan lonjakan MAPE hingga >300%, sementara **Huber Regressor** tetap stabil dengan MAPE di kisaran 131%. 


## 👥 Kelompok 8

1. Aliya Raffa Naura Ayu
2. Natalie Grace Katiandagho 
3. Naila Hanifah 



---

**Cara Menjalankan:**

1. Pastikan library `pandas`, `numpy`, `sklearn`, `matplotlib`, dan `seaborn` terinstall.
2. Letakkan file dataset di folder yang sama.
3. Jalankan perintah: `python "untitled9 (1).py"`

---

