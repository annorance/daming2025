# Tugas Akhir Mata Kuliah Data Mining (KOM1338)

Sebagai bagian dari tugas MK Data Mining, setiap mahasiswa diminta untuk mengikuti dan mengerjakan kompetisi Data Mining yang telah disediakan di https://www.kaggle.com/competitions/kom-1338-data-mining-prediksi-status-kelulusan/overview. Setiap mahasiswa juga diwajibkan untuk menuliskan laporan dalam dokumen maksimal 2 halaman tentang metode dan model yang digunakan. Laporan juga harus disertai dengan kode program serta model yang dibuat.

## Dataset Description
Data set yang digunakan merupakan data yang diambil dari paper berjudul: "Predicting Student Dropout and Academic Success" (Valoriza et. al, 2022) https://www.mdpi.com/2306-5729/7/11/146. Semua file (training set, test set serta submission Anda) berupa file CSV dengan kolom pertama bernama sample_id (nomor pengamatan). Terdapat 4000 pengamatan pada data training, dan sekitar 400 pengamatan pada data uji. Terdapat 34 fitur: dari Marital Status sampai dengan GDP yang dapat digunakan untuk memprediksi kelas target. Ada 3 kemungkinan kelas target yaitu: Enrolled (masih kuliah), Graduated (lulus), dan Dropout (DO). 

Anda dapat membaca arti/makna untuk fitur yang bersifat kategorik dapat dibaca disini: https://github.com/carmelh/SQL_projects/tree/main/student_data_analysis/Datasets

### Columns
* sample_id - nomor sample
* Marital status&nbsp;s/d GDP - semua fitur yang dapat digunakan
* Target - Kelas yang harus diprediksi.

## Evaluation
Setiap submission Anda akan dievaluasi menggunakan metrik 'Akurasi'

## Submission File
Untuk setiap sample_id pada data test, Anda harus memprediksi nilai Target (Enrolled, Graduate, Dropout)

---

## Citation
Mushthofa IPB. KOM1338 Data Mining - Prediksi Status Kelulusan. https://kaggle.com/competitions/kom-1338-data-mining-prediksi-status-kelulusan, 2025. Kaggle.
