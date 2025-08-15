# CAPSTONE-3-JCDS-2702----PRADNA-AQMARIL-PARAMITHA

## 1. Project Overview
Sebuah hotel di Portugal mengumpulkan informasi pemesanan yang berisi data mengenai tamu, baik dari dalam negeri maupun luar negeri. Dari sejumlah tamu tersebut, ada yang melakukan pembatalan kamar hotel (cancellation). Hotel ingin mengetahui tamu mana yang kemungkinan besar akan membatalkan pemesanan mereka. Informasi terkait demografi tamu, jenis reservasi, lama menginap, dan sumber pemesanan tersedia dari data booking.

Pembatalan pemesanan kamar hotel dapat menyebabkan kerugian pendapatan yang signifikan serta alokasi sumber daya yang tidak efisien. Memahami faktor-faktor yang mempengaruhi pembatalan sangat penting bagi manajemen hotel untuk menerapkan strategi yang dapat mengurangi pembatalan dan meningkatkan efisiensi operasional.

Jika hotel tidak dapat memprediksi kemungkinan pembatalan, mereka mungkin akan mengalami masalah overbooking, persediaan kamar yang tidak optimal, dan biaya operasional tambahan akibat pembatalan yang tidak terduga.

### Target:
0 : Tidak membatalkan kamar hotel
1 : Membatalkan kamar hotel

### Tujuan
Membuat model machine learning untuk hotel yang memiliki kemampuan untuk memprediksi apakah sebuah pemesanan akan dibatalkan atau tidak. Dengan kemampuan prediksi ini, hotel dapat:
1. Mengoptimalkan alokasi kamar dan sumber daya.
2. Mengurangi kerugian pendapatan akibat pembatalan mendadak.
3. Mengetahui faktor-faktor utama yang menyebabkan tamu membatalkan pemesanan sehingga dapat merancang strategi mitigasi, seperti kebijakan pembatalan atau promosi khusus.

## 2. Sumber Data
- [Hotel Booking Data](https://drive.google.com/drive/folders/17KIeOXK7eYGuzgpn_IljlUFcE4v96lSL) (booking information for a hotel located in Portugal, and includes information regarding room reservation for respective customers. All personally identifying information has been removed from the data.

## 3. Technologies Used
- Programming Language: Python (e.g., Pandas, NumPy)
- Visualization: Matplotlib, Seaborn, Plotly
- Version Control: Git
- Others: Jupyter Notebook
- ...

## 4. Project Structure

```
├── README.md          <- The top-level README for developers using this project.
├── data
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- CAPSTONE 3 JCDS 2702-Pradna Aqmaril Paramitha.ipynb
```

## 5. Rangkuman Kesimpulan
### 5.1 Business Insight
Bila seandainya biaya kerugian akibat pembatalan kamar (False Negative) sekitar $150 per kamar dan biaya yang hilang akibat memprediksi pemesanan akan dibatalkan padahal tidak (False Positive) sekitar $45 per kamar, maka hitungannya kurang lebih akan seperti ini, dengan asumsi jumlah pemesanan dalam suatu periode adalah 200 pemesanan (100 dibatalkan, 100 tidak dibatalkan):

Tanpa Model (semua pemesanan diasumsikan berisiko dibatalkan dan perlu mitigasi):
- Total Biaya = 200 x $45 = $9,000 (biaya mitigasi untuk semua pemesanan)
- Total Pemesanan yang benar-benar dibatalkan yang ditangani = 100 orang (karena semua diasumsikan berisiko)
- Total Pemesanan yang dibatalkan tapi tidak ditangani = 0 orang
- Biaya yang terbuang = 100 x $45 = $4,500 (untuk pemesanan yang sebenarnya tidak dibatalkan tetapi tetap diasumsikan berisiko)
- Jumlah penghematan = 0 USD

Dengan Model Gradient Boosting (menggunakan prediksi setelah tuning):
- Total Pemesanan yang diprediksi berisiko dibatalkan = 450 + 605 = 1,055 pemesanan (dari confusion matrix, skala disesuaikan ke 200 pemesanan → proporsional)
- Total Biaya ≈ (pemenuhan FN) + (biaya FP)
    - FN (pemesanan dibatalkan tapi tidak diprediksi dibatalkan) = 29 → 29 x $150 = $4,350
    - FP (pemesanan tidak dibatalkan tapi diprediksi dibatalkan) = 605 → proporsional: 605 / 1,538 ≈ 78% → 78 x $45 ≈ $3,510
- Total Biaya ≈ $4,350 + $3,510 = $7,860
- Total Pemesanan dibatalkan yang benar-benar ditangani = 450 → proporsional: 450 / 479 ≈ 94% dari pemesanan dibatalkan
    -Pemesanan dibatalkan yang tidak ditangani = 29 → 6%
- Biaya yang terbuang untuk pemesanan yang tidak dibatalkan = $3,510
- Jumlah penghematan dibanding tanpa model = $4,500 - $3,510 ≈ $990

Berdasarkan perhitungan tersebut, terlihat bahwa dengan menggunakan model Gradient Boosting yang sudah dituning, hotel dapat:
1. Memenuhi target performa dengan F2 Score ≥ 0,7 pada data validasi dan mengidentifikasi 3–5 fitur utama yang paling berpengaruh terhadap pembatalan.
2. Menangkap sebagian besar pemesanan berisiko dibatalkan (recall 94% untuk kelas 1) sehingga dapat diambil tindakan mitigasi tepat waktu.
3. Mengurangi biaya yang terbuang akibat False Positive dibandingkan strategi tanpa model, dengan estimasi penghematan sekitar $990 per periode (asumsi 200 pemesanan).
4. Mendukung strategi pengurangan kerugian minimal 10% melalui prediksi yang dapat ditindaklanjuti secara nyata.### 5.2 Actionable Recommendation
   
### 5.1 Rekomendasi Bisnis
1. Kebijakan pembayaran awal (misalnya deposit sebagian) untuk pemesanan yang diprediksi memiliki risiko pembatalan tinggi, guna mengurangi kerugian finansial.
2. Penawaran ulang kamar (reselling) untuk pemesanan berisiko tinggi yang dibatalkan, dengan memanfaatkan sistem booking online atau partner OTA.
3. Peningkatan komunikasi proaktif kepada tamu berisiko tinggi, seperti pengingat via email/SMS atau penawaran diskon kecil jika tamu mengonfirmasi kembali kedatangannya.
4. Fleksibilitas penjadwalan untuk mengalihkan pembatalan menjadi pemesanan ulang pada tanggal lain, mengurangi kehilangan pendapatan langsung.
5. Menetapkan target pengurangan kerugian minimal 10% sebagai indikator keberhasilan penerapan strategi pencegahan berbasis prediksi model.
   
## 6. Contact
- Name: Pradna Aqmaril Paramitha
- Email: pparamitha0712@gmail.com
- Linkedin: ([Pradna Aqmaril Paramitha](https://www.linkedin.com/in/pparamitha))
