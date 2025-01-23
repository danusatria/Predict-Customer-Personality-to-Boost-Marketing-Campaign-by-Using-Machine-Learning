![myriam-jessier-eveI7MOcSmw-unsplash](https://github.com/user-attachments/assets/27fe5e25-fc5e-4cfb-8cdf-fa4af121d17e)

## Problem Statemnet
### Background
Sebuah perusahaan dapat berkembang dengan pesat saat mengetahui perilaku customer personality nya, sehingga dapat memberikan layanan serta manfaat lebih baik kepada customers yang berpotensi menjadi loyal customers. Dengan mengolah data historical marketing campaign guna menaikkan performa dan menyasar customers yang tepat agar dapat bertransaksi di platform perusahaan, dari insight data tersebut fokus kita adalah membuat sebuah model prediksi kluster sehingga memudahkan perusahaan dalam membuat keputusan.

### Goal
Tujuan utama dari project ini adalah untuk memanfaatkan data pelanggan untuk meningkatkan kinerja bisnis secara keseluruhan. Dengan memahami pelanggan lebih baik, perusahaan dapat memberikan pengalaman pelanggan yang lebih baik, meningkatkan penjualan, dan membangun merek yang kuat.

### Objective
- Dengan menggunakan algoritma K-Means, saya akan mengklasifikasikan pelanggan ke dalam segmen-segmen yang berbeda.
- Mendapatkan pemahaman yang lebih mendalam tentang karakteristik unik dari setiap kelompok pelanggan.
- Memanfaatkan hasil analisis ini untuk merancang langkah-langkah bisnis yang lebih efektif.

## Data 
### Data Overview
- Dataset terdiri dari 2240 baris, 28 fitur.
- Dataset terdiri dari 3 tipe data; float64, int64, dan objek
- Kolom Dt_Customer dapat diubah menjadi tipe data datetime
- Dataset berisi 24 Nilai Null dari fitur Income

### Feature Engineering
Pada tahap feature engineering, dilakukan pembuatan feature baru berdasarkan feature yang sudah ada dengan tujuan untuk membuat analisis menjadi lebih insightful. Feature baru ini dapat mengungkap informasi tambahan atau menggabungkan beberapa fitur yang saling berhubungan untuk membentuk fitur yang lebih kuat.
1. Total_Acc_Cmp : AcceptedCmp1 + AcceptedCmp2 + AcceptedCmp3 + AcceptedCmp4 + AcceptedCmp5
3. Total_Spending : MntCoke + MntFruits + MntMeatProducts + MntFishProducts + MntSweet
4. Total_Transaction : NumDealsPurchases + NumWebPurchases + NumCatalogPurchases + NumStorePurchases
5. Conversion_Rate : Total_Transaction / NumWebVisitsMonth
6. Age : 2024 - Year_Birth
7. Age_Category: Segmentasi dari kolom Age menjadi 3 kategori.
8. Membership_Duration = 2024 - Dt_Customer
9. Total_Children : Kidhome + Teenhome

## Data Analysis

### Univariate Analysis 
#### Numierical Columns
![image](https://github.com/user-attachments/assets/bad1c9c7-75b1-4628-ab92-9b4dc17ef93a)
Terdapat outlier pada beberapa kolom diantaranya :
'Year_birth', 'Income', 'MntCoke', 'MntFruits', 'MntMeatProducts', 'MntFishProducts', 'MntSweetProducts', 'MntGoldProds', 'NumDealsPurchases', 'NumWebPurchases', 'NumCatalogPurchases', 'NumWebVisitsMonth', 'Total_Transaction', 'Total_Spending', 'Conversion_Rate', 'Age'.
Yang selanjutnya kolom kolom tersebut akan dilakukan penghapusan outliers.
   
#### Categorical Columns
![image](https://github.com/user-attachments/assets/19b05d39-16dc-48b5-8026-41c4fc2dd632)
Customer didominasi dengan educataion S1, status pernikahan menikah, dan kategori usia Middle-Aged Adults.

### Bivariate Analysis
#### Conversion rate by age category
![image](https://github.com/user-attachments/assets/9690f92c-1378-4b6c-a714-0b675b06d5e8)
Berdasarkan plot diatas terdapat hubungan yang signifikan antara conversion rate dengan age category. Dimana kategori young adult memilki convertion rate yang sangat rendah (3.58%) jika dibandingkan dengan kategori Midle-Aged Adults (43.02%) dan Senior(53.40%).

#### Convertion Rate VS Age, Income, Total Spending
![image](https://github.com/user-attachments/assets/0efb38e2-26bb-44d0-a538-662f15030d77)
Conclusion :
- Age dan conversion rate :
  Terlihat korelasi positif lemah antara umur dan tingkat konversi. Semakin bertambah usia, tingkat konversi cenderung meningkat, tetapi hubungan ini tidak terlalu kuat.Ini bisa berarti bahwa usia yang lebih tua sedikit lebih cenderung untuk terlibat atau berkonversi, mungkin karena stabilitas finansial atau preferensi belanja tertentu.
- Income dan conversion rate :
  Hubungan korelasi positif kuat antara pendapatan (Income) dan tingkat konversi. Hal ini menunjukan bahwa semakin tinggi pendapatan, tingkat konversi cenderung meningkat. Ini menunjukkan bahwa pelanggan dengan pendapatan lebih tinggi lebih cenderung terlibat atau melakukan pembelian.
- Total spending dan conversion rate :
  Korelasi positif yang kuat antara pengeluaran total (Total Spending) dan tingkat konversi. Hal ini menunjukan bahwa pelanggan dengan pengeluaran lebih tinggi juga menunjukkan tingkat konversi yang lebih tinggi. Hubungan ini bisa menunjukkan bahwa pelanggan dengan keterlibatan yang lebih besar pada kampanye pemasaran memiliki pengeluaran yang lebih besar, sehingga meningkatkan Conversion Rate.
Strategi pemasaran bisa difokuskan pada pelanggan dengan pendapatan dan pengeluaran tinggi, karena mereka memiliki peluang konversi lebih besar.

#### Age VS Income, Total Spending
![image](https://github.com/user-attachments/assets/395740a0-a09f-4447-8f05-9552f2913de8)
Conclusion :
- Age dan Income : Terdapat hubungan positif antara pendapatan (Income) dan usia (Age). Korelasi ini tidak sangat kuat, mengindikasikan faktor lain seperti tingkat pendidikan atau pekerjaan juga berpengaruh.
- Age dan Total spending : Ada hubungan positif lemah antara total pengeluaran (Total Spending) dan usia (Age). Usia yang lebih tua cenderung dihubungkan dengan pengeluaran yang sedikit lebih tinggi. Namun, hubungan ini lebih lemah dibandingkan dengan "Income vs Age", yang menunjukkan bahwa pengeluaran tidak selalu sebanding dengan usia.
Strategi pemasaran bisa diarahkan pada segmen usia yang lebih tua (50 ke atas) dengan pendapatan tinggi, karena mereka memiliki potensi untuk pengeluaran lebih besar.

### Multivariate Analysis
![image](https://github.com/user-attachments/assets/f071ff8c-b976-4e01-a45a-e091ce8afdd9)
Conclusion :
- Middle-Aged Adults adalah kelompok dominan dalam pendapatan, pengeluaran, dan tingkat konversi.
- Ada hubungan positif yang kuat antara pendapatan, pengeluaran, dan tingkat konversi, tetapi dengan variasi yang lebih tinggi di beberapa kategori usia.
- Young Adults dan Seniors cenderung memiliki nilai yang lebih rendah dibandingkan Middle-Aged Adults.

Suggestion :
1. Fokus pada Middle_Age Adult sebagai segmen utama :
   - Buat kampanye pemasaran yang ditagetkan pada segmen ini.
   - Tawarkan produk atau layanan premium sesuai daya beli mereka.
   - Perkuat loyalitas dengan program member, diskon eksklusif, penawaran berbasis langganan.
2. Membuat strategi khusus untuk segmen senior :
   - Kembangkan layanan yang memprioritaskan kenyamanan dan kebutuhan mereka(misalnya, layanan berbasis kesehatan atau kenyamanan).
   - Gunakan pendekatan pemasaran yang lebih personal, seperti konsultasi langsung atau pemasaran offline.
   - Optimalkan hubungan pendapatan, tigkat pembelian, dan konversi :
3. Buat program upselling dan cross-selling untuk mendorong pengeluaran pelanggan.
   - Tawarkan insentif berbasis pengeluaran (contoh: "Dapatkan diskon jika belanja lebih dari X").
   - Gunakan data analitik untuk mengidentifikasi pelanggan bernilai tinggi dan tingkatkan konversi mereka.


## Data Preprocessing
#### Menangani Null Value
Ternapat 24 nilai null pada kolom Income, karena data tersebut 1% dari total data maka dilakukan penghapusan.

#### Menangani Outlier
Terdapat outlier pada beberapa kolom diantaranya :
  
['Year_birth', 'Income', 'MntCoke', 'MntFruits', 'MntMeatProducts', 'MntFishProducts', 'MntSweetProducts', 'MntGoldProds', 'NumDealsPurchases', 'NumWebPurchases', 'NumCatalogPurchases', 'NumWebVisitsMonth', 'Total_Transaction', 'Total_Spending', 'Conversion_Rate', 'Age']
  
Yang selanjutnya kolom kolom tersebut akan dilakukan penghapusan outliers.

#### Encoding Feature
Melakukan encoding pada kolom Education.

#### Menghapus kolom yang tidak diperlukan
Beberapa kolom seperti 'Unnamed: 0', 'ID', 'Year_Birth', 'Education', 'Marital_Status', 'Age_Category', 'Dt_Customer'. Tidak diperlukan / sudah dilakukan feature engineering, sehingga kolom kolom tersebut dapat dihapus.

#### Feature Scaling
Fitur numerik diskalakan menggunakan StandardScaler() Scikit-Learn untuk tujuan pengelompokan.

## Modeling
Setelah data dibersihkan dan disiapkan, langkah selanjutnya adalah menggunakan teknik PCA untuk meringkas data. PCA akan membantu kita memilih data yang paling penting dan mengurangi jumlah variabel tanpa kehilangan informasi yang berarti. Kemudian, kita akan menentukan jumlah kelompok pelanggan yang paling tepat dengan melihat grafik Distortion Score dan Elbow Method. Hasilnya, kita menemukan bahwa pelanggan dapat dibagi menjadi 4 kelompok utama.
![image](https://github.com/user-attachments/assets/97c27827-b20b-4cf1-bccd-67a08902e173)

Setelah kita tahu berapa banyak kelompok yang paling sesuai, kita mulai mengelompokkan data menggunakan metode K-means. Metode ini akan membagi data menjadi kelompok-kelompok berdasarkan kesamaan ciri. Dengan begitu, kita bisa melihat pola-pola yang muncul dan memahami karakteristik dari setiap kelompok.
![image](https://github.com/user-attachments/assets/70fb77f1-bd4d-417b-aec2-c7e7e279cf7a)
Visualisasi hasil clustering menunjukkan pemisahan yang jelas antar cluster, mengindikasikan keberhasilan algoritma dalam mengidentifikasi struktur laten dalam data. Setiap cluster mewakili kelompok data dengan karakteristik yang homogen.

#### Evaluasi
![image](https://github.com/user-attachments/assets/b13c558a-a8b5-4d38-a756-39d038292888)
Kesimpulan :
- Berdasarkan Silhouette Score, jumlah cluster terbaik yang direkomendasikan adalah 4.
- Hasil Clustering: Sebagian besar data dikelompokkan dengan baik (silhouette coefficient positif), meskipun ada beberapa data dengan nilai negatif.
- Rata-rata Silhouette: Garis merah menunjukkan hasil clustering cukup baik (mendekati atau melebihi 0.5).

## Customer Personality Analysis
Setelah mengelompokkan pelanggan, langkah selanjutnya adalah mencari tahu apa saja perbedaan dan persamaan antar kelompok. Dengan begitu, kita bisa memahami karakteristik unik dari setiap kelompok pelanggan dan menyesuaikan strategi bisnis kita agar lebih pas dengan kebutuhan masing-masing kelompok.
  
![image](https://github.com/user-attachments/assets/554d1cec-70f8-4234-bb2f-f7e031fd0060)
Kalau kita lihat grafik hubungan antara pendapatan dan pengeluaran, kelompok pelanggan 0 dan 3 terlihat mirip. Ini artinya, pelanggan di kedua kelompok ini punya kebiasaan belanja dan penghasilan yang hampir sama.

![image](https://github.com/user-attachments/assets/aa6fbd19-f661-482f-8a72-85158cced987)
Conclusion : Berdasarkan hasil clustering, diketahui bahwa :
1. Cluster 0
   - Rata rata transaksi di cluster 0 dan cluster 2 berada di angka yang sama diangka 21 transaksi.
   - Total spending cukup sedang diangka Rp 816.000/bulan.
   - Income berada di nilai yang cukup tinggi diangka Rp 62.551.500/tahun.
   - Convension rate tertinggi, senilai 5%.
   - Mayoritas usia 60 tahun.
2. Cluster 1
   - Total transaksi terendah, diangka 7 transaksi.
   - Total spending terendah, diangka Rp 54.000/bualn.
   - Income terendah diangka Rp 32.233.000/tahun.
   - Conversion rate terendah, senilai 1%.
   - Mayoritas usia 51 tahun.
3. Cluster 2
   - Rata rata transaksi di cluser 2 sama dengan cluster 0 diangka 21 transaksi.
   - Total spending dan total income tertinggi, dengan total spending senilai Rp 1.217.000/bulan dan income Rp 74.290.000/tahun.
   - Convesion rate cukup tinggi diangka 4%.
   - Mayoritas usia 57 tahun.
4. Cluster 3
   - Rata rata transaksi cukup sedang diangka 15 transaksi.
   - Total spending cukup sedang cinderung rendah diangka Rp 311.000/bulan.
   - Total Income cukup sedang cinderung rendah diangka Rp 49.176.500/tahun.
   - Conversion rate cinderung rendah diangka 2%.
   - Mayoritas usia 59 tahun.
Kesimpulan :
- Cluster 0 : High transaction, high spending, high income. (High Customer 1)
- Cluster 1 : Low transaction, low spending, low income. (Low Customer )
- Cluster 2 : High transaction, high spending, high income. (High Customer 2)
- Cluster 3 : Moderate transaction, moderate spending, moderate income. (Moderate Customer)

![image](https://github.com/user-attachments/assets/cf16ca94-8fce-45dd-be0e-acdcfefb3d40)
Business Insight :
- Lebih dari 50% customer berada di cluster low, dengan total transaksi yang rendah, total spending rendah, serta pendapatan rendah. Meskipun demikian, perusahaan harus memperhatikan cluster ini karena tingginya populasi.
- Cluster 0 dan 2 termasuk dalam high cluster, namun populasinya rendah sehingga perusahaan harus mempertimbangkan strategi pemasaran untuk mempertahankan loyalitas cluster ini.

![image](https://github.com/user-attachments/assets/b74b071d-d91a-4f0b-b9bb-0526d9139efc)
Insight :
- Cluster 1 memiliki NumVisitsMonth yang paling tinggi namun dengan TotalSpending terendah. Hal ini menunujkan bahwa mereka sangat sering mengunjungi website namun tidak melakukan transaksi. Perusahaan harus memperhatikan fenomena ini mengingat cluster ini adalah cluster dengan populasi yang paling besar sehingga perusahaan perlu mengembangkan strategi untuk menarik perhatian mereka.
- Cluster 2 memiliki tingkat accept campaign yang paling besar, cluster ini juga memilki total spending yang paling besar. Hal ini menunjukan bahwa mereka sangat sensitif terhadap campain yang ditawarkan namun terlihat juga bahwa mereka memiliki NumVisitsMonth yang rendah dengan kata lain mereka jarang membuka website. Dengan ini perusahaan dapat memaksimalkan promosi dengan mengubungi melalui email, whatsapp, atau media lainnya agar mampu menjangkau segmen ini.
- Cluster 3 memiliki spending, visit month, dan conversion rate yang semua berada di nilai rata-rata. Pelanggan ini berpotensi untuk ditingkatkan kontribusinya (potential growth) dengan cara analisis tambahan untuk memahami apa yang mendorong perilaku belanja mereka seperti preferensi produk, memberikan penawaran yang relevan secara personal seperti memberi diskon tambahan untuk pembelian berulang, dan memberikan program loyalitas yang menarik.

## Recomendation
Dari hasil analisis, kita dapat mengenali karakteristik atau profil pelanggan berdasarkan kluster yang ada. Memahami karakteristik ini sangat penting untuk merancang strategi pemasaran yang lebih tepat sasaran. Dengan mengetahui preferensi, kebutuhan, dan perilaku konsumen di setiap kluster, perusahaan dapat menciptakan kampanye yang lebih relevan dan menarik bagi masing-masing kelompok pelanggan.

#### Cluster 1 (Low Customer - Low Transaction, Low Spending, Low Income):
- Memiliki proporsi pelanggan terbesar (lebih dari 50%).
- Mayoritas pelanggan berada dalam kategori ini, yang berarti sebagian besar basis pelanggan memiliki kemampuan dan aktivitas ekonomi yang rendah.
- Insight Bisnis:
  - Strategi pemasaran dan promosi yang terjangkau dapat diutamakan untuk kelompok ini.
  - Berikan edukasi atau penawaran khusus untuk meningkatkan transaksi dan loyalitas pelanggan.
  - Identifikasi peluang untuk meningkatkan pendapatan mereka (misalnya, melalui layanan kredit kecil atau bundling produk).

#### Cluster 0 (High Customer 1 - High Transaction, High Spending, High Income):
- Proporsi pelanggan ini lebih kecil dibandingkan Cluster 1, tetapi lebih signifikan dibandingkan Cluster 2.
- Insight Bisnis:
  - Fokus pada layanan premium atau eksklusif untuk mempertahankan pelanggan ini.
  - Peluang untuk cross-selling atau up-selling produk dengan margin lebih tinggi.
  - Perhatikan loyalitas mereka melalui program VIP atau reward khusus.

#### Cluster 2 (High Customer 2 - High Transaction, High Spending, High Income):
- Proporsi pelanggan sangat kecil (di bawah 5%).
- Insight Bisnis:
  - Kelompok ini merupakan segmen potensial dengan nilai tinggi; perlu dilakukan analisis lebih mendalam untuk memahami kebutuhan mereka.
  - Investasi dalam mempertahankan pelanggan ini sangat penting karena kontribusi mereka terhadap pendapatan perusahaan bisa signifikan.

#### Cluster 3 (Moderate Customer - Moderate Transaction, Moderate Spending, Moderate Income):
- Memiliki proporsi pelanggan yang cukup besar setelah Cluster 1 (sekitar 20%-30%).
- Insight Bisnis:
  - Segmen ini dapat diarahkan untuk meningkatkan pengeluaran mereka melalui promosi produk atau layanan yang sesuai dengan daya beli mereka.
  - Berikan pengalaman yang lebih personal untuk menarik mereka menuju Cluster 0 atau 2.
