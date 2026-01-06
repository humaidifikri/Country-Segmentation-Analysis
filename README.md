
# 🌍 Country Segmentation Analysis for International Aid Allocation

Proyek ini bertujuan untuk mengelompokkan negara-negara di dunia berdasarkan indikator sosial-ekonomi dan kesehatan menggunakan algoritma **Unsupervised Learning**. Hasil analisis ini dimaksudkan untuk membantu organisasi internasional (seperti NGO atau PBB) dalam menentukan prioritas pemberian bantuan secara objektif dan berbasis data.

## 📊 Dataset Overview

Dataset terdiri dari data 167 negara dengan 10 fitur utama:
-   **Kesehatan:** `child_mort` (kematian anak), `health` (pengeluaran kesehatan), `life_expec` (harapan hidup), `total_fer` (tingkat kesuburan).
   
-   **Ekonomi:** `income`, `inflation`, `gdpp` (GDP per capita), `exports`, `imports`.
    

## 🛠️ Tech Stack

-   **Language:** Python, Jupyter Notebook
    
-   **Libraries:** 
	-  `Pandas` & `NumPy` (Data Manipulation)
    
    -   `Scikit-Learn` (Scaling & Clustering)
        
    -   `Matplotlib` & `Seaborn` (Data Visualization)
        
    -   `Yellowbrick` (Model Evaluation - Optional)
        

## 🚀 Key Workflow

### 1. Preprocessing & EDA

-   Pengecekan _missing values_ dan _outliers_.
    
-   **Feature Scaling:** Menggunakan `StandardScaler` untuk menyamakan skala fitur karena algoritma berbasis jarak (KMeans/DBSCAN) sangat sensitif terhadap perbedaan satuan.
    

### 2. Model Evaluation (Finding K)

-   **Elbow Method:** Mencari titik di mana penurunan _Inertia_ mulai melandai.
    
-   **Silhouette Score:** Digunakan untuk memvalidasi seberapa baik pemisahan antar cluster (Skor optimal ditemukan pada $k=3$ atau $k=5$ tergantung kebutuhan spesifisitas).
    

### 3. Clustering Algorithms

Proyek ini mengeksplorasi dua pendekatan:

-   **K-Means Clustering:** Untuk pengelompokan berbasis centroid yang stabil.

## 📈 Cluster Interpretations

Berdasarkan analisis profiling, negara dikelompokkan menjadi:

#### Cluster 0 – Negara menuju Maju
- **Rata-rata Income per Kapita**: 12,679
- **Rata-rata GDP per Kapita**: 6,494
- **Rata-rata Angka Kematian Bayi**: 22.22
- **Rata-rata Harapan Hidup**: 72.63 tahun
- **Rata-rata Total Fertility Rate**: 2.33

**Analisis**:
Cluster ini mencakup negara-negara dengan tingkat pembangunan menengah. Pendapatan dan GDP per kapita sudah relatif baik, disertai dengan harapan hidup yang cukup tinggi dan angka kematian bayi yang mulai menurun. Negara-negara dalam cluster ini umumnya berada pada fase transisi pembangunan, di mana kualitas hidup meningkat namun masih menghadapi tantangan seperti inflasi, ketimpangan sosial, dan efisiensi layanan publik.

#### Cluster 1 – Negara Maju

- **Rata-rata Income per Kapita**: 44,022
- **Rata-rata GDP per Kapita**: 42,119
- **Rata-rata Angka Kematian Bayi**: 5.18
- **Rata-rata Harapan Hidup**: 80.08 tahun
- **Rata-rata Total Fertility Rate**: 1.79

**Analisis**:
Cluster ini merepresentasikan negara-negara dengan tingkat pembangunan sangat tinggi. Pendapatan dan GDP per kapita besar, angka kematian bayi sangat rendah, serta harapan hidup tinggi. Negara dalam cluster ini memiliki sistem kesehatan dan ekonomi yang matang, stabilitas makroekonomi yang baik, serta kualitas hidup yang tinggi. Tantangan utama bukan lagi pertumbuhan, melainkan penuaan penduduk dan keberlanjutan sistem sosial.

#### Cluster 2 – Negara Berkembang dengan Tantangan Struktural

- **Rata-rata Income per Kapita**: 3,503
- **Rata-rata GDP per Kapita**: 1,754
- **Rata-rata Angka Kematian Bayi**: 94.31
- **Rata-rata Harapan Hidup**: 59.02 tahun
- **Rata-rata Total Fertility Rate**: 5.05

**Analisis**:
Cluster ini mencakup negara-negara dengan tingkat kesejahteraan rendah dan tantangan pembangunan yang serius. Pendapatan dan GDP per kapita rendah, disertai dengan angka kematian bayi yang tinggi serta tingkat fertilitas yang besar. Kondisi ini mencerminkan keterbatasan akses terhadap layanan kesehatan, pendidikan, dan infrastruktur dasar, serta tekanan demografis yang tinggi terhadap perekonomian.

#### Cluster 3 – Negara dengan Kondisi Ekstrem

- **Rata-rata Income per Kapita**: 5,150
- **Rata-rata GDP per Kapita**: 2,330
- **Rata-rata Angka Kematian Bayi**: 130.00
- **Rata-rata Harapan Hidup**: 60.50 tahun
- **Rata-rata Inflasi**: 104.00

**Analisis**:
Cluster ini menggambarkan negara-negara dengan kondisi ekonomi dan sosial yang sangat tidak stabil. Inflasi yang sangat tinggi, angka kematian bayi ekstrem, serta rendahnya aktivitas perdagangan menunjukkan adanya krisis struktural. Negara-negara dalam cluster ini umumnya menghadapi permasalahan serius seperti konflik, ketidakstabilan politik, atau kegagalan kebijakan ekonomi.

#### Cluster 4 – Negara Super Kaya

- **Rata-rata Income per Kapita**: 64,033
- **Rata-rata GDP per Kapita**: 57,567
- **Rata-rata Angka Kematian Bayi**: 4.13
- **Rata-rata Harapan Hidup**: 81.43 tahun
- **Rata-rata Ekspor**: 176.00

**Analisis**:
Cluster ini mencakup negara-negara dengan tingkat pendapatan tertinggi dan keterbukaan perdagangan yang sangat besar. Harapan hidup sangat tinggi dan angka kematian bayi sangat rendah menunjukkan kualitas hidup yang sangat baik. Perekonomian negara dalam cluster ini sangat bergantung pada perdagangan internasional, keuangan global, atau sumber daya strategis, sehingga sangat sensitif terhadap dinamika ekonomi global.
    

## 💡 Business Recommendations

### 1. Prioritas Utama: Intervensi Kemanusiaan (Cluster 3 & 2)

Kelompok ini merupakan target utama untuk bantuan hibah dan program darurat.

-   **Cluster 3 (Kondisi Ekstrem):**
    
    -   **Stabilisasi Makroekonomi:** Fokus pada bantuan teknis untuk meredam inflasi ekstrem (104%) melalui reformasi kebijakan moneter.
        
    -   **Bantuan Darurat Medis:** Prioritaskan program penurunan angka kematian bayi yang mencapai 130.00 (tertinggi) melalui penyediaan vaksin dan sanitasi dasar.
        
-   **Cluster 2 (Tantangan Struktural):**
    
    -   **Program Keluarga Berencana:** Mengingat _Fertility Rate_ yang tinggi (5.05), perlu edukasi reproduksi untuk menekan tekanan demografis pada ekonomi.
        
    -   **Peningkatan Infrastruktur Dasar:** Investasi pada akses air bersih dan pendidikan dasar untuk menaikkan Harapan Hidup yang saat ini masih di bawah 60 tahun.
        

### 2. Pendorong Pertumbuhan & Investasi (Cluster 0)

Negara-negara ini berada dalam fase transisi pembangunan dan paling cocok untuk kerjasama ekonomi komersial.

-   **Cluster 0 (Menuju Maju):**
    
    -   **Investasi Infrastruktur & Digital:** Fokus pada peningkatan efisiensi layanan publik dan konektivitas untuk mengatasi tantangan ketimpangan sosial.
        
    -   **Penguatan Sektor Manufaktur:** Dengan GDP per Kapita menengah ($6,494), negara-negara ini adalah pasar yang potensial untuk ekspansi industri dan perdagangan skala menengah.
        

### 3. Aliansi Strategis & Keberlanjutan (Cluster 1 & 4)

Kelompok ini adalah penyedia modal (investor) dan mitra dagang utama global.

-   **Cluster 1 (Negara Maju):**
    
    -   **Sektor Layanan Lansia (Silver Economy):** Fokus pada inovasi teknologi kesehatan dan sistem pensiun berkelanjutan untuk menghadapi penuaan penduduk.
        
    -   **Investasi ESG:** Mendorong investasi pada ekonomi hijau dan keberlanjutan sebagai pemimpin standar global.
        
-   **Cluster 4 (Negara Super Kaya):**
    
    -   **Diversifikasi Ekonomi:** Mengurangi ketergantungan ekstrem pada perdagangan internasional agar lebih tangguh terhadap guncangan global.
        
    -   **Hub Logistik & Keuangan:** Memperkuat posisi sebagai pusat keuangan global atau jalur ekspor-impor utama dunia.
