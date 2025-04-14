# 📊 Predictive Analytics: Klasifikasi Status Gizi Balita

## 🗂️ Domain Proyek

Malnutrisi masih tetap menjadi permasalahan utama pada bayi dan anak di bawah lima tahun (balita) secara global. Stunting merupakan salah satu permasalahan gizi utama pada balita di Indonesia yang sampai saat ini belum teratasi.  Prevalensi stunting di Indonesia berdasarkan WHO masih menjadi masalah kesehatan masyarakat yaitu diatas 20%. Penyebab stunting multifaktorial dan berkaitan dengan asupan gizi yang kurang atau kebutuhan gizi yang meningkat. Stunting memiliki dampak jangka pendek dan jangka panjang yang irreversible. Bahkan sampai saat ini masih belum ada panduan nasional pelayanan kesehatan untuk balita stunting[1].

Stuntingadalah kondisi dimana balita memiliki panjang atau tinggi badan yang kurang jika dibandingkan dengan umur. Kondisi ini di ukur dengan panjang atau tinggibadan yang lebih dari minus dua median standar pertumbuhan anak dari World Health Organization(WHO). Faktor penyebab stunting terdiri dari faktor ekonomi, pendidikan ibu, tinggi badan ibu, ASI eksklusif, usia anak dan BBLR (Berat Badan Lebih Rendah). Tujuan Untuk mengetahui faktor-faktor yang mempengaruhi terjadinya stunting pada anak balita. Metode Penelitian yang dilakukan adalah Literature Reviewdengan desain Narrative Review. Hasil yaitu Berdasarkan 5 penelitian didapatkan bahwa fakor risiko penyebabterjadinya stunting berdasarkan Berat Badan Lahir Rendah (BBLR) merupakan faktor yang paling berhubungan dengan penyebab terjadinya stunting. Faktor Usia tersering penyebab pertambahan jumlah stunting pada  balita  ialah  kisaran  usia  6-24  bulan.  Faktor  Jenis  kelamin  laki-laki  memiliki  prevalensi  terhadap  kejadian stuntingpada balita dibandingkan dengan perempuan. Kesimpulan Faktor penyebab terjadinya stuntingpada  balita  di  dapatkan  bahwa  faktor  berat  badan  lahir  rendah (BBLR),usia,  jenis  kelamin, tingkat  pendidikan ibu,  status  ekonomi  dan  pelayanan  kesehatan  balita  merupakan  faktor  risiko  penyebab terjadinya stuntingpada balita. [2]

Melalui analisis data status gizi balita, kita dapat memahami variabel apa saja yang berkontribusi signifikan terhadap kondisi tersebut, sehingga membantu dalam perancangan kebijakan intervensi yang lebih akurat dan tepat sasaran.

**Referensi:**
- [1] Kementerian Kesehatan Republik Indonesia. (2022). Keputusan Menteri Kesehatan Republik Indonesia Nomor HK.01.07/MENKES/1928/2022 tentang Pedoman Nasional Pelayanan Kedokteran Tatalaksana Stunting. Jakarta: Kementerian Kesehatan Republik Indonesia.
- [2]Tebi, K. Dahlia, E. A. Wello, I. Safei, Rahmawati, S. Juniarty, dan A. Kadir, “Literature Review Faktor-Faktor yang Mempengaruhi Terjadinya Stunting pada Anak Balita,” Fakultas Kedokteran, Universitas Muslim Indonesia, Makassar, Indonesia. [Online]

---

## 💼 Business Understanding

### 🧩 Problem Statements
- Apa saja faktor utama yang memengaruhi status gizi balita?
- Dapatkah status gizi balita diprediksi secara akurat menggunakan algoritma machine learning?

### 🎯 Goals
- Membangun model klasifikasi untuk memprediksi status gizi balita.
- Mengetahui fitur penting yang berkontribusi dalam prediksi status gizi.

### 💡 Solution Statement
1. **Baseline Model**: Decision Tree Classifier
2. **Alternatif Model**: Random Forest dan XGBoost Classifier

**Metrik Evaluasi:**
- Accuracy
- Precision
- Recall
- F1-score

---

## 📊 Data Understanding

### 📁 Dataset
- **Sumber**: [Dataset Stunting Toddler (Balita) Detection](https://raw.githubusercontent.com/agummds/Predictive-Analytics/master/Dataset/data_balita.csv)
- **Jumlah Data**: ±121.000 baris
- **Jumlah Fitur**: 4 kolom

### 🔍 Deskripsi Fitur

| Nama Fitur         | Tipe Data | Deskripsi                                                             |
|--------------------|-----------|----------------------------------------------------------------------|
| `Umur (Bulan)`     | numerik   | Usia balita dalam bulan (0–60 bulan)                                 |
| `Jenis Kelamin`    | kategori  | Kategori: laki-laki atau perempuan                                   |
| `Tinggi Badan`     | numerik   | Tinggi badan balita dalam centimeter                                 |
| `Status Gizi`      | kategori  | Kategori target: severely stunting, stunting, normal, tinggi         |

## 📈 Exploratory Data Analysis (EDA)

### A. Univariate Analysis
---
### a. Distribusi Status Gizi

![Distribusi Status Gizi](https://drive.google.com/uc?export=view&id=1zmPKHg9EqTyHUK6ol5K0JutS6opAy_ms)

### 🔍 Insight dari Visualisasi

1. **Kategori Normal Mendominasi**
   - Balita dengan status gizi *normal* mencapai sekitar 68.000 kasus.
   - Ini berarti lebih dari setengah populasi memiliki kondisi gizi yang baik.

2. **Masalah Stunting Masih Signifikan**
   - Gabungan kategori *stunted* dan *severely stunted* mencapai sekitar 30.000 kasus.
   - Sekitar 25% data menunjukkan masalah gizi kronis yang perlu perhatian khusus.

3. **Kategori Tinggi Juga Menonjol**
   - Sekitar 20.000 balita masuk kategori *tinggi*, hampir sebanding dengan jumlah kasus stunting.

### b. Umur (bulan) — numerik
![Distribusi Umur](https://drive.google.com/uc?export=view&id=1D91G2sCBgpwlIkefTWl5LfnrmJLGuupV)

### 🔍 Insight dari Visualisasi

1. **Distribusi Umur Merata**
   - Mayoritas balita tersebar merata dalam rentang usia 0–59 bulan.
   - Dataset cukup representatif terhadap semua kelompok umur.

2. **Lonjakan pada Usia 60 Bulan**
   - Terdapat puncak jumlah data pada usia 60 bulan.
   - Kemungkinan disebabkan pencatatan massal pada usia maksimum balita.

3. **Penurunan pada Usia 9–11 Bulan**
   - Penurunan kecil pada rentang ini bisa menunjukkan ketidakseimbangan data atau bias dalam pengumpulan informasi.
### c. Tinggi Badan (cm) — numerik
![Boxplot Tinggi Badan](https://drive.google.com/uc?export=view&id=1196RHZYXBBTbFzIEwmaaZAN9ysJlycLy)

### 🔍 Insight dari Visualisasi

1. **Sebaran Tinggi Badan Luas**
   - Tinggi badan berkisar antara 40 cm hingga 130 cm.
   - Mewakili rentang usia balita yang luas.

2. **Median Tinggi Badan Sekitar 95–100 cm**
   - Nilai tengah distribusi berada di kisaran tinggi anak usia 2–4 tahun.

3. **Outlier pada Nilai Rendah**
   - Terdapat outlier sekitar 40 cm yang bisa mewakili bayi baru lahir atau potensi data error.

4. **Distribusi Simetris**
   - Tampilan boxplot menunjukkan distribusi tinggi badan yang relatif seimbang.

### d. Jenis Kelamin — kategorikal
### Distribusi Jenis Kelamin
![Distribusi Jenis Kelamin](https://drive.google.com/uc?export=view&id=1ZY8RvrfUN7lQ_KVC49pBWKWCgcMUV5MS)

### 🔍 Insight dari Visualisasi

1. **Distribusi Seimbang**
   - Balita laki-laki berjumlah sekitar 60.000.
   - Balita perempuan berjumlah sekitar 61.000.
   - Tidak ada ketimpangan besar antara keduanya.

2. **Data Representatif**
   - Keseimbangan ini penting untuk menjaga fairness model dalam prediksi.
   - Tidak ada indikasi bias gender dalam distribusi data.
---
## B. Multivariate Analysis EDA
### a. Umur vs Tinggi Badan (scatter plot)
![Umur vs Tinggi Badan](https://drive.google.com/uc?export=view&id=1VK5ppK7hrQNhhM8WepAsmvx-bN085Hrp)

### 🔍 Insight dari Visualisasi

1. **Tinggi Badan Meningkat Seiring Bertambahnya Umur**
   - Semua kategori menunjukkan pola pertumbuhan yang positif sesuai usia balita.

2. **Pemisahan Status Gizi Jelas**
   - Kategori seperti *tinggi*, *normal*, *stunted*, dan *severely stunted* membentuk pola sendiri-sendiri yang tidak saling tumpang tindih secara signifikan.
   - Visual ini mendukung keandalan label untuk klasifikasi.

3. **Tinggi vs Severely Stunted**
   - Anak dengan status *tinggi* memiliki tinggi badan lebih dominan sepanjang usia.
   - *Severely stunted* menunjukkan pertumbuhan yang paling rendah secara konsisten.

4. **Distribusi Konsisten hingga 60 Bulan**
   - Tidak terlihat anomali atau stagnasi pada distribusi tinggi badan, yang menandakan dataset cukup baik.

### b. Jenis Kelamin vs Status Gizi (countplot with hue)
![Distribusi Status Gizi per Jenis Kelamin](https://drive.google.com/uc?export=view&id=1FprAoIR4nc5yGJIb4Ds_NbN6j8yqq_H4)
### 🔍 Insight dari Visualisasi

1. **Status Gizi Normal Mendominasi**
   - Baik laki-laki maupun perempuan mayoritas masuk dalam kategori *normal*.
   - Laki-laki sedikit lebih unggul dalam jumlah anak dengan gizi normal.

2. **Distribusi Cenderung Seimbang**
   - Semua kategori status gizi memiliki jumlah yang relatif seimbang antara jenis kelamin.
   - Tidak ditemukan ketimpangan signifikan antara laki-laki dan perempuan.

3. **Kategori Tinggi Sedikit Lebih Banyak pada Perempuan**
   - Anak perempuan sedikit lebih banyak berada dalam kategori *tinggi* dibanding laki-laki, meski perbedaannya tipis.
     
### c.  Boxplot Tinggi Badan berdasarkan Status Gizi
![Tinggi Badan per Kategori Status Gizi](https://drive.google.com/uc?export=view&id=1XwK_yvuuy60C6tq7n8AI4ioXOUpLvtZA)

### 🔍 Insight dari Visualisasi

1. **Tinggi Badan Berkorelasi dengan Status Gizi**
   - Anak dengan status gizi *tinggi* memiliki tinggi badan paling tinggi secara median maupun sebaran.
   - Sebaliknya, anak dengan status *severely stunted* memiliki tinggi paling rendah.

2. **Sebaran Tinggi Lebih Luas di Kategori Normal dan Tinggi**
   - Menunjukkan variasi tinggi badan yang lebih besar pada anak-anak yang tergolong sehat atau sangat sehat.

3. **Outlier di Setiap Kategori**
   - Adanya nilai ekstrem (outlier) di semua kategori menunjukkan bahwa meskipun pola umum terlihat jelas, ada kasus khusus yang perlu diperhatikan lebih lanjut.
---
## 🧹 Data Preparation

**1. Load Dataset**
```
url = 'https://raw.githubusercontent.com/agummds/Predictive-Analytics/master/Dataset/data_balita.csv'
df = pd.read_csv(url)
```
- Menggunakan `pd.read_csv()` untuk mengambil data dari URL.
- Tujuannya agar data siap dianalisis lebih lanjut.

**2. Eksplorasi Struktur Data**
```
df.head(20)
df.tail()
df.info()
df.describe()
```
- Fungsi `head()`, `info()`, dan `describe()` digunakan untuk memahami bentuk dan kualitas data.
- Untuk memahami skema dan kualitas data, serta mendeteksi potensi masalah seperti missing values.

**3. Encoding Data Kategori**
```
le_gender = LabelEncoder()
le_status = LabelEncoder()

df_encoded['Jenis Kelamin'] = le_gender.fit_transform(df_encoded['Jenis Kelamin'])
df_encoded['Status Gizi'] = le_status.fit_transform(df_encoded['Status Gizi'])
```
- `LabelEncoder` diterapkan pada kolom `Jenis Kelamin` dan `Status Gizi`.
- Ini penting karena model prediktif memerlukan input numerik.

**4. Duplikasi DataFrame**
- `df_encoded = df.copy()` untuk menjaga versi asli tetap utuh.

**5. Analisis Korelasi**

![Encode kolom kategorikal dan cek korelasi](https://drive.google.com/uc?export=view&id=1-6KPZt1qv7PX2bULatPf-a_KZvgpZa7G)
```
corr = df_encoded.corr()
sns.heatmap(corr, annot=True, cmap='coolwarm')

```
- Korelasi antar variabel dianalisis menggunakan heatmap.
- Membantu memahami hubungan antar fitur, mendeteksi redundansi 
---
## 🤖 Modeling

### 📌 Algoritma yang Digunakan
- Decision Tree Classifier
- Random Forest Classifier
- XGBoost Classifier

### ⚙️ Tahapan dan Parameter Modeling
- **Splitting Data**: 80% training, 20% testing
- **Preprocessing**:
  - LabelEncoder untuk kolom 'Status Gizi' dan 'Jenis Kelamin'
- **Model & Parameter**:
  - DecisionTreeClassifier(random_state=42)
  - RandomForestClassifier(random_state=42)
  - XGBClassifier(random_state=42)

### 📊 Evaluasi Model
- Accuracy
- Confusion Matrix
- Classification Report (Precision, Recall, F1-score)
- Bar chart perbandingan akurasi

### ✅ Kelebihan dan Kekurangan

#### Decision Tree
- ✅ Cepat dan sederhana
- ❌ Mudah overfitting

#### Random Forest
- ✅ Bagus untuk generalisasi
- ❌ Waktu training lebih lama

#### XGBoost
- ✅ Akurasi tinggi, powerful
- ❌ Komputasi kompleks

### 🏆 Model Terbaik
- **Random Forest** dipilih karena memberikan hasil akurasi terbaik dari ketiga model.


Model terbaik adalah **Random Forest** dengan hasil evaluasi:
- **Accuracy**: >99%
- **Precision**: Tinggi
- **Recall**: Konsisten
- **F1-score**: Seimbang across classes
---
## 📊 Evaluation

### 🔧 Metrik Evaluasi yang Digunakan

Proyek ini menggunakan dua metrik utama:

- **Accuracy**: Mengukur seberapa besar proporsi prediksi benar dari seluruh data.
- **Confusion Matrix**: Memberikan rincian benar/salah prediksi berdasarkan masing-masing kelas.

### 📈 Hasil Evaluasi

| Model           | Accuracy |
|----------------|----------|
| Decision Tree  | 0.999174     |
| Random Forest  | 0.999215     |
| XGBoost        |  0.990455    |

Meskipun Decision Tree dan Random Forest memiliki akurasi sempurna, perlu diperhatikan kemungkinan overfitting, terutama bila diuji pada data baru.

### 📌 Confusion Matrix

Label kelas:
- 0 = Normal
- 1 = Tinggi
- 2 = Stunted
- 3 = Severely Stunted

Model menunjukkan performa sangat baik dalam mengklasifikasikan keempat kelas. Kesalahan yang terjadi cenderung kecil dan mayoritas prediksi sesuai.

### 🧠 Insight

- Fitur yang digunakan sangat informatif.
- Model menunjukkan kemampuan prediksi yang tinggi.
- Tetap perlu evaluasi lebih lanjut dengan data unseen untuk memastikan generalisasi model.

## ✅ Kesimpulan

Proyek ini telah berhasil mengembangkan model machine learning untuk memprediksi **status gizi balita** berdasarkan variabel-variabel seperti **umur**, **jenis kelamin**, dan **tinggi badan**. Hasil eksplorasi data, visualisasi, dan pemodelan menghasilkan beberapa kesimpulan penting:

### 📌 Faktor-faktor utama yang memengaruhi status gizi balita:
- **Umur balita** — Berkorelasi dengan pertumbuhan tinggi badan secara alami.
- **Tinggi badan** — Indikator utama dalam klasifikasi status gizi (`stunted`, `normal`, `tinggi`, dan `severely stunted`).
- **Jenis kelamin** — Tidak terlalu signifikan, namun menunjukkan perbedaan kecil dalam distribusi status gizi.

### 🤖 Model Machine Learning yang Dikembangkan:
- **Decision Tree**
- **Random Forest**
- **XGBoost**

### 🧪 Hasil Evaluasi:
- **Decision Tree** dan **Random Forest** mencapai **akurasi 100%**
- **XGBoost** mencapai **akurasi 99%**
- **Random Forest** dipilih sebagai model terbaik berdasarkan:
  - Akurasi tinggi dan stabil
  - Kemampuan generalisasi
  - Hasil confusion matrix yang menunjukkan klasifikasi yang sangat akurat

Confusion matrix memperlihatkan bahwa **mayoritas status gizi berhasil diklasifikasikan dengan benar**, dan kesalahan klasifikasi sangat kecil. Ini menunjukkan bahwa model mampu **menangkap pola data dengan sangat baik**.

Kesimpulannya, **machine learning dapat menjadi alat bantu skrining status gizi yang efektif**, khususnya bagi tenaga kesehatan yang membutuhkan sistem deteksi dini berbasis data sederhana.

---

## 🚀 Rekomendasi Pengembangan Lanjutan

1. **Melakukan cross-validation** dan fine-tuning hyperparameter secara lebih ekstensif untuk menguji kestabilan model.
2. **Menambahkan dataset agar ada fitur tambahan** seperti:
   - Berat badan
   - Riwayat kesehatan ibu
   - Status ekonomi keluarga
3. **Mengembangkan sistem digital** berbasis web atau mobile untuk mempermudah asesmen status gizi oleh tenaga medis di lapangan.
4. **Menguji model pada data dari wilayah/populasi berbeda** untuk melihat performa dan kemampuan generalisasi lintas daerah.

---
## 📚 Referensi

- Kementerian Kesehatan Republik Indonesia. (2022). Keputusan Menteri Kesehatan Republik Indonesia Nomor HK.01.07/MENKES/1928/2022 tentang Pedoman Nasional Pelayanan Kedokteran Tatalaksana Stunting. Jakarta: Kementerian Kesehatan Republik Indonesia.
- Tebi, K. Dahlia, E. A. Wello, I. Safei, Rahmawati, S. Juniarty, dan A. Kadir, “Literature Review Faktor-Faktor yang Mempengaruhi Terjadinya Stunting pada Anak Balita,” Fakultas Kedokteran, Universitas Muslim Indonesia, Makassar, Indonesia.
- [Scikit-learn Documentation](https://scikit-learn.org)
- [XGBoost Documentation](https://xgboost.readthedocs.io)
