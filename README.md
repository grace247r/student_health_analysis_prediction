# 🏥 Student Health Condition Prediction Model

Model prediksi kondisi kesehatan mahasiswa berbasis **Machine Learning**, dibangun menggunakan Python dan Scikit-learn. Proyek ini menganalisis pengaruh faktor gaya hidup dan fisiologis terhadap kondisi kesehatan mahasiswa, sekaligus membangun model klasifikasi untuk memprediksinya.

---

## 📋 Deskripsi

Proyek ini menggabungkan **Exploratory Data Analysis (EDA)** dan **Machine Learning** untuk mengklasifikasikan kondisi kesehatan mahasiswa ke dalam tiga kategori:

- 🟢 **Fit** — kondisi kesehatan baik
- 🟡 **At-Risk** — berisiko mengalami gangguan kesehatan
- 🔴 **Unhealthy** — kondisi kesehatan buruk

Tiga algoritma klasifikasi dibandingkan secara sistematis menggunakan cross-validation, lalu model terbaik dievaluasi dan diinterpretasikan menggunakan permutation importance.

---

## 📊 Dataset

| Atribut | Detail |
|---|---|
| **File** | `enhanced_student_health_dataset_50k.xls` |
| **Jumlah Data** | 50,000 records |
| **Target** | `health_condition` (Fit / At-Risk / Unhealthy) |

### Variabel dalam Dataset

**Fisiologis:** `bmi`, `heart_rate`, `sleep_duration`, `stress_level`

**Gaya Hidup:** `physical_activity_level`, `screen_time`, `stress_relief_activities`

**Temporal:** `timestamp` (jam, hari, bulan)

**Target:** `health_condition`

---

## 🔍 Alur Proyek

### 1. Exploratory Data Analysis (EDA)
- Distribusi kondisi kesehatan mahasiswa
- Pengaruh BMI, detak jantung, durasi tidur, dan screen time terhadap kondisi kesehatan (boxplot)
- Heatmap proporsi aktivitas fisik & stress level vs. kondisi kesehatan
- Matriks korelasi fitur gaya hidup & fisiologis
- Distribusi kondisi kesehatan berdasarkan hari dan jam

### 2. Preprocessing
- Encoding variabel kategorik dengan `LabelEncoder`
- Penanganan missing values dengan `SimpleImputer`
- Standarisasi fitur dengan `StandardScaler`
- Split data: **80% training / 20% testing** (stratified)

### 3. Model Training & Evaluasi
Tiga model dibandingkan dengan **5-Fold Stratified Cross-Validation:**

| Model | Keterangan |
|---|---|
| Logistic Regression | Baseline linear classifier |
| Random Forest | Ensemble 200 trees, max_depth=15 |
| Gradient Boosting | 150 estimators, learning_rate=0.1 |

### 4. Evaluasi Model Terbaik
- Classification report (precision, recall, F1-score)
- Confusion matrix
- **Permutation Feature Importance** — Top 10 fitur paling berpengaruh

---

## 🛠️ Teknologi yang Digunakan

- **Python 3**
- **Pandas & NumPy** — manipulasi data
- **Matplotlib & Seaborn** — visualisasi
- **Scikit-learn** — preprocessing, model training, evaluasi

---

## 💡 Hasil & Temuan

### 🏆 Performa Model

| Model | Accuracy | Keterangan |
|---|---|---|
| **Random Forest** | **~99%** | Model terbaik — menangkap pola non-linear dengan sangat baik |
| Logistic Regression | ~70% | Baseline yang layak, namun kesulitan pada kelas *unhealthy* |
| Gradient Boosting | — | Dijalankan pada notebook lengkap |

Random Forest jauh unggul dibanding Logistic Regression karena data memiliki hubungan non-linear yang kuat antar fitur. Logistic Regression kesulitan mengklasifikasikan kelas **Unhealthy** (recall hanya 25%), sedangkan Random Forest mencapai F1-score 92% untuk kelas yang sama.

---

### 🔑 Fitur Paling Berpengaruh (Feature Importance)

| Rank | Fitur | Importance |
|---|---|---|
| 1 | `stress_level` | 23.8% |
| 2 | `mental_health_status` | 21.6% |
| 3 | `sleep_duration` | 21.0% |
| 4 | `academic_pressure` | 11.1% |
| 5 | `physical_activity_level` | 10.6% |
| 6 | `screen_time` | 6.5% |

Tiga faktor teratas — **stres, kesehatan mental, dan durasi tidur** — bersama-sama menyumbang lebih dari 65% dalam menentukan kondisi kesehatan mahasiswa.

---

### 📌 Insight Utama dari EDA

- **Stress level adalah prediktor terkuat:** 82.6% mahasiswa dengan kondisi *unhealthy* memiliki stress level tinggi, dibandingkan hanya 10.8% pada mahasiswa *fit*.

- **Status kesehatan mental sangat menentukan:** 84.4% mahasiswa *unhealthy* memiliki mental health status *poor*, sedangkan 87% mahasiswa *fit* berada di kategori *moderate* atau *stable*.

- **Tekanan akademik berpengaruh signifikan:** 61.2% mahasiswa *unhealthy* menghadapi tekanan akademik tinggi, vs. hanya 21.3% pada mahasiswa *fit*.

- **Gaya hidup sedentari berisiko:** 60.1% mahasiswa *unhealthy* termasuk kategori *sedentary* (aktivitas fisik rendah), sementara mahasiswa *fit* lebih banyak di kategori *active* dan *moderate*.

- **Tidur lebih singkat pada mahasiswa tidak sehat:** rata-rata tidur mahasiswa *fit* adalah **7.4 jam/hari**, *at-risk* **6.7 jam**, dan *unhealthy* hanya **5.7 jam**.

- **Faktor yang tidak berpengaruh signifikan:** diet type, smoking status, dan alcohol intake menunjukkan distribusi yang hampir merata di semua kategori kesehatan — artinya faktor psikologis dan aktivitas fisik lebih dominan dari kebiasaan konsumsi dalam dataset ini.

---

## 👤 Author

Dibuat oleh *[Grace L.R. Pangaribuan]* — *[Data Science]*

---

## 📄 Lisensi

Proyek ini dibuat untuk tugas akhir mata kuliah Data Science.
