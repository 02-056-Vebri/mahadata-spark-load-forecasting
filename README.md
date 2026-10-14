# Replikasi Parsial: Load Forecasting dengan Apache Spark (Low Carbon London)

Tugas Eksplorasi Mandiri Mahadata (IF25-40402), Institut Teknologi Sumatera.
Penulis: Vebri Yanti (NIM 123140056)

## Tujuan
Mereplikasi sebagian alur kerja Ali, Alham, & Ibrahim (2024)
(https://doi.org/10.1186/s40537-024-00909-6): peramalan konsumsi listrik
dengan PySpark MLlib menggunakan regresi Plain, Ridge, Lasso, Elastic Net,
dan Decision Tree Regressor. Eksperimen dijalankan pada dua skenario data,
yaitu PENUH dan TERPOTONG.

## Struktur repositori
- `Vebri_Yanti_123140056_Tugas_Mahadata_1.ipynb` : seluruh alur (pengunduhan data, pembersihan, agregasi, fitur cuaca dan hari libur, pelatihan model)
- `hasil_semua.csv` : tabel hasil (R², MAE, MSE, RMSE, waktu latih dan uji) untuk data PENUH dan TERPOTONG
- `requirements.txt` : versi pustaka

## Lingkungan
- Google Colab, Python 3.13.16
- PySpark 3.5.5 (mode lokal), pandas 2.2.3, NumPy 2.1.3

## Cara menjalankan
1. Buka notebook di Google Colab (tautan di bagian atas notebook).
2. Jalankan sel secara berurutan dari atas ke bawah: pasang PySpark, unduh data, pembersihan, agregasi, cuaca, hari libur, lalu sel model.
3. Sel model membutuhkan sekitar 10-20 menit. Hasil akhir tersimpan di `hasil_semua.csv`.

## Sumber data
- Konsumsi listrik: Low Carbon London, UK Power Networks (data terbuka), diambil dari dataset Kaggle "Smart Meters in London" melalui kagglehub. Subset yang dipakai: half-hourly dataset `block_0` (50 rumah, 1.222.670 baris, Des 2011 - Feb 2014).
- Cuaca: `weather_hourly_darksky.csv` (data cuaca per jam dari DarkSky), dalam dataset Kaggle yang sama.
- Hari libur: `uk_bank_holidays.csv` (hari libur resmi Inggris), dalam dataset Kaggle yang sama; rentang data 1 Februari 2012 - 26 Desember 2014.

## Catatan
- Replikasi bersifat parsial: dijalankan pada subset data dengan Spark mode lokal.
- File hari libur tidak mencakup Desember 2011 sampai Januari 2012, sehingga fitur hari libur pada periode awal hanya menangkap akhir pekan.
