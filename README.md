# Adidas Sales Performance Analysis

### Pengantar
Dalam industri ritel seperti Adidas, pemantauan kinerja penjualan secara rutin merupakan hal yang krusial. Performa penjualan dapat dipengaruhi oleh berbagai faktor, seperti perbedaan performa antar retailer, kontribusi penjualan di tiap wilayah, serta variasi produk dan metode penjualan yang digunakan. Faktor-faktor ini dapat berdampak signifikan terhadap total penjualan maupun profit yang diperoleh. Oleh karena itu, pendekatan berbasis data diperlukan untuk memahami bagaimana tren penjualan berkembang. 

Proyek ini menggunakan data penjualan produk Adidas tahun 2020 dan 2021 untuk menganalisis pola penjualan bulanan. Hasil analisis diharapkan dapat memberikan insight yang berguna dalam mendukung strategi peningkatan penjualan di masa mendatang.

### Tujuan
Tujuan dari analisis ini adalah untuk menganalisis data penjualan Adidas tahun 2020–2021 serta mengidentifikasi insight yang dapat mendukung peningkatan performa penjualan dan optimalisasi strategi bisnis. Melalui analisis ini, dapat diketahui faktor-faktor yang memengaruhi penjualan, mengidentifikasi tren utama, serta menemukan peluang pertumbuhan di masa mendatang.

### Sumber Data
Proyek ini menggunakan dataset penjualan Adidas berasal dari [Kaggle](https://www.kaggle.com/datasets/ahmedabbas757/dataset) yang berisi catatan detail transaksi penjualan produk dari Januari 2020 hingga Desember 2021. Dataset ini terdiri dari 6.641 baris dan 12 kolom, di mana setiap baris merepresentasikan satu transaksi penjualan. Adapun kolom-kolom dalam database tersebut, yaitu:
- Retailer : Perusahaan atau individu yang menjual produk Adidas langsung kepada konsumen.
- Retailer ID : Nomor identitas unik yang diberikan kepada setiap retailer di dalam dataset.
- Invoice Date : Tanggal terjadinya transaksi penjualan atau penerbitan faktur.
- Region : Wilayah geografis tertentu tempat berlangsungnya aktivitas penjualan.
- State : Provinsi atau divisi administratif dalam suatu negara tempat penjualan dilakukan.
- City : Kota atau daerah perkotaan tempat aktivitas penjualan dilakukan.
- Product : Jenis atau kategori produk Adidas yang dijual.
- Price per Unit : Harga yang ditetapkan untuk setiap satuan produk.
- Units Sold : Jumlah unit produk yang terjual dalam suatu transaksi.
- Total Sales : Total pendapatan yang diperoleh dari transaksi penjualan.
- Operating Profit : Keuntungan yang diperoleh retailer dari aktivitas penjualan utamanya.
- Sales Method : Cara atau saluran yang digunakan retailer untuk menjual produknya (misalnya, toko fisik, online, atau melalui mitra).

### Data Preparation
Raw dataset diimpor menggunakan library Pandas di Python. Setelah itu dilakukan beberapa tahap pembersihan data agar hasil analisis lebih akurat dan konsisten, di antaranya:
1. Menghapus kolom-kolom yang tidak akan digunakan dalam analisis diantaranya, yaitu kolom Retailer ID, Region, dan City.
2. Menangani missing values dan juga menghapus baris dengan harga 0 karena kemungkinan besar merepresentasikan barang retur atau penjualan yang direfund.
3. Mengubah kolom Invoice Date ke dalam format datetime, kemudian dilakukan ekstraksi untuk menghasilkan kolom Month dan Year
4. Melakukan standarisasi pada kolom Product karena terdapat kesalahan penulisan untuk produk yang sama, misalnya "Men's aparel" harusnya "Men's Apparel"
5. Menghapus karakter khusus seperti tanda dolar ($) dan koma (,) pada kolom bernilai uang (Price per Unit, Total Sales, dan Operating Profit). Selain itu, mengubah kolom-kolom tersebut ke tipe data numerik.

### Exploratory Data Analysis (EDA)
#### Bagaimana tren penjualan produk Adidas per bulan selama tahun 2020–2021?
<img width="1489" height="590" alt="image" src="https://github.com/user-attachments/assets/2cae1634-cd97-43f9-8f22-2fa35c81597f" />

Berdasarkan tren bulanan, total revenue Adidas mengalami peningkatan pesat dari 2020 ke 2021. Pada tahun 2020, total revenue seb tercatat sebesar $18.022.475, sedangkan pada 2021 mencapai $71.726.592. Sepanjang 2020,  total revenue relatif rendah dan cenderung berfluktuasi kecil, dengan titik terendah pada Desember 2020 sebesar $746.654. Akan tetapi, pada Januari 2021 terlihat lonjakan signifikan yang menjadi awal pemulihan penjualan. Selama 2021, tren penjualan mengalami peningkatan tajam dengan kinerja yang jauh lebih kuat dibandingkan tahun sebelumnya. Puncak penjualan terjadi pada Juli 2021 dan kembali meningkat menjelang akhir tahun, sejalan dengan pola musiman seperti periode liburan dan promosi.

Karena pada tahun 2021 revenue Adidas mengalami peningkatan tajam sebagai bagian dari masa pemulihan, maka analisis kinerja pada berbagai aspek akan difokuskan pada data tahun 2021 saja.

#### Retailer mana yang memiliki kinerja penjualan yang kuat?
<img width="835" height="470" alt="image" src="https://github.com/user-attachments/assets/7040f58b-ed13-49ee-9b3a-5a38af97d393" />

Berdasarkan hasil analisis, retailer dengan total revenue tertinggi pada tahun 2021 adalah Foot Locker dengan nilai sebesar $17.701.839, diikuti oleh Sports Direct sebesar $16.721.043 dan West Gear sebesar $15.230.797. Ketiga retailer ini menjadi kontributor utama revenue Adidas pada tahun tersebut. Sementara itu, Kohl’s dan Amazon berada pada kategori menengah dengan masing-masing sekitar $10.135.656 juta dan $7.769.912 juta. Adapun Walmart mencatat revenue paling rendah, yakni hanya sekitar $4.167.345 juta, sehingga kontribusinya relatif kecil dibanding retailer lainnya.

<img width="1492" height="590" alt="image" src="https://github.com/user-attachments/assets/9e4d7962-a40b-4195-8a02-ba5a46b4fbc5" />

Selain itu, berdasarkan analisis profit bulanan tahun 2021, Foot Locker menunjukkan kinerja paling stabil dengan tren kenaikan sepanjang tahun dan mencapai puncak profit tertinggi pada Desember sebesar $1.001.620 sehingga dapat dianggap sebagai retailer dengan kontribusi profit paling konsisten. Sports Direct mencatat profit tertinggi pada September sebesar $1.280.350, namun cenderung sangat fluktuatif, mengindikasikan adanya pengaruh promosi musiman atau kampanye khusus. Di sisi lain, Walmart tercatat sebagai retailer dengan profit paling rendah sepanjang tahun, meskipun sempat mengalami peningkatan di pertengahan tahun.

Secara keseluruhan, baik dari sisi revenue maupun profit, retailer dengan performa terbaik didominasi oleh beberapa pemain besar, khususnya Foot Locker, Sports Direct, dan West Gear, sementara retailer lainnya memberikan kontribusi yang relatif kecil.

#### Produk mana yang memiliki performance penjualan terbaik?
<img width="693" height="455" alt="image" src="https://github.com/user-attachments/assets/e463db54-d29a-4308-a06b-6777272ef9ac" />

Produk dengan penjualan tertinggi adalah Men’s Street Footwear yang hampir mencapai 500.000 unit, menunjukkan dominasi tren streetwear di pasar. Diikuti oleh Women’s Apparel dan Men’s Athletic Footwear yang masing-masing mencatat lebih dari 350.000 unit terjual, serta Women’s Street Footwear dengan lebih dari 300.000 unit. Sementara itu, Men’s Apparel dan Women’s Athletic Footwear menjadi kategori dengan penjualan terendah.

<img width="1490" height="590" alt="image" src="https://github.com/user-attachments/assets/69d8e824-1e87-4e03-9090-bd082e469459" />

Men’s Street Footwear menjadi produk dengan profit tertinggi dan paling konsisten, terutama pada bulan Juli ($744.827) dan Desember ($753.562). Sebaliknya, Women’s Athletic Footwear mencatat profit terendah sepanjang tahun. Hal ini menunjukkan adanya perbedaan preferensi pasar antara kategori produk, di mana produk street footwear lebih mendominasi dibanding produk athletic footwear.

#### Produk apa dengan unit terjual tertinggi per retailer?

<img width="1119" height="590" alt="image" src="https://github.com/user-attachments/assets/fd03c5c1-cf39-4303-b0fe-d0d68dca1a1e" />

Men’s Street Footwear mendominasi sebagai produk dengan unit terjual tertinggi di hampir semua retailer, terutama di Foot Locker (129.998 unit) dan Sports Direct (115.395 unit). Sementara itu, Walmart mencatat volume penjualan yang relatif rendah di semua kategori, dengan produk terlarisnya hanya Men’s Street Footwear sebanyak 24.650 unit. Hal ini menegaskan bahwa produk street footwear menjadi kategori paling populer lintas retailer, sedangkan apparel cenderung memiliki performa lebih rendah dibandingkan kategori sepatu.

#### State mana yang mencatat total revenue tertinggi?

<img width="828" height="449" alt="image" src="https://github.com/user-attachments/assets/7f999424-0376-41ac-997a-05c498f0e9d2" /> 

California menjadi state dengan total revenue tertinggi pada tahun 2021, mencapai $5.110.735. Angka ini jauh melampaui state lain di posisi berikutnya seperti South Carolina sebesar $2.928.565 dan Florida sebesar $2.768.290. Sementara New York dan North Carolina kontribusi keduanya terhadap revenue masing-masing mencapai $2.442.784 dan $2.395.657. Hal ini menunjukkan bahwa California merupakan pasar paling potensial dengan kontribusi terbesar terhadap total revenue perusahaan.

#### Produk mana yang mencatat penjualan tertinggi di lima state dengan total revenue terbesar?

<img width="1113" height="590" alt="image" src="https://github.com/user-attachments/assets/43db3bfc-b315-4156-b3f3-c0b989e81742" />

Men’s Street Footwear menjadi produk dengan unit terjual tertinggi di semua state dengan revenue terbesar, khususnya di California mencapai 27.325 unit. Produk ini konsisten unggul di Florida, New York, North Carolina, dan South Carolina. Sementara itu, produk dengan penjualan relatif rendah di setiap state adalah Women’s Athletic Footwear, misalnya di California hanya 21.131 unit dan di New York 7.850 unit. Hal ini menunjukkan bahwa produk  street footwear, khususnya untuk pria, lebih mendominasi preferensi konsumen dibandingkan kategori athletic footwear.

#### Metode penjualan apa yang menunjukkan performance terbaik?

<img width="449" height="470" alt="image" src="https://github.com/user-attachments/assets/be9d25ea-2985-4736-90dd-edd1b1f3f009" />

Penjualan di toko fisik (in-store) memberikan kontribusi terbesar terhadap total revenue tahun 2021, yaitu 36,6% atau sebesar $26.274.076. Penjualan secara online menyusul dengan kontribusi 33,9% ($24.315.426), sedangkan penjualan melalui outlet menyumbang 29,5% ($21.137.094). Meskipun in-store masih menjadi metode dominan, distribusi revenue dari ketiga metode penjualan ini relatif seimbang.

<img width="567" height="455" alt="image" src="https://github.com/user-attachments/assets/372954a8-c28c-45f4-8344-312dbf913d04" />

Dari grafik tersebut terlihat bahwa produk yang dijual melalui online merupakan penjualan tertinggi pada 2021 mencapai 852.008 unit. mencapai  metode penjualan online. Selanjutnya, disusul oleh penjualan melalui outlet dengan jumlah produk terjual yaitu sebesar 630.089 unit. Sementara penjualan di toko fisik (in-store) sebesar 540.000 unit.

Hal ini menunjukkan bahwa meskipun penjualan di toko fisik (in-store) memberikan kontribusi revenue terbesar, dari sisi volume produk yang terjual, penjualan online lebih unggul. Dengan kata lain, online berperan penting dalam mendorong kuantitas penjualan, sedangkan in-store lebih kuat dalam memberikan nilai transaksi yang lebih tinggi per produk.

#### Metode penjualan apa yang menghasilkan operating profit terbesar di masing-masing retailer?

<img width="990" height="489" alt="image" src="https://github.com/user-attachments/assets/3f897d45-f8be-482c-97b9-404cd5f7ac41" />

Terlihat bahwa setiap retailer memiliki metode penjualan yang berbeda-beda sebagai sumber profit terbesar. Amazon dan Foot Locker memperoleh profit terbesar dari penjualan Online  yang menunjukkan keunggulan mereka di ranah digital. Sedangkan Kohl’s dan Sports Direct justru lebih banyak menghasilkan profit dari Outlet, yang menunjukkan keberhasilan strategi diskon dan penjualan melalui outlet fisik. Walmart meskipun skala profitnya relatif kecil dibanding retailer lain, penjualan Online tetap menjadi penyumbang profit terbesar. Sementara itu, West Gear menjadi satu-satunya retailer yang masih sangat bergantung pada In-store, dengan kontribusi profit yang jauh lebih besar dibanding kanal lain.

### Dashboard Summary
![Dashboard Adidas-1_1](https://github.com/user-attachments/assets/22a1a71e-ac09-424b-a940-1b91bd38b83f)

### Rekomendasi
Berdasarkan hasil Exploratory Data Analysis (EDA) yang dilakukan, rekomendasi yang dapat diberikan, yaitu:
1. **Prioritaskan Retailer dengan Profit Konsisten**. Foot Locker terbukti sebagai retailer paling stabil dalam menyumbang profit. Perusahaan sebaiknya memperkuat kemitraan dengan strategi khusus, seperti penawaran produk eksklusif atau kampanye bersama.
2. **Fokus pada produk dengan profit tertinggi**. Men’s Street Footwear terbukti menjadi produk paling konsisten dalam menghasilkan profit, khususnya di bulan Juli dan Desember. Perusahaan sebaiknya mempertahankan stok, promosi, dan strategi distribusi produk ini agar kontribusinya tetap optimal.
3. **Optimalkan produk dengan penjualan rendah**. Women’s Athletic Footwear menunjukkan profit terendah. Strategi seperti penyesuaian harga, paket bundling, atau promosi khusus bisa diterapkan untuk meningkatkan daya tarik produk ini.
4. **Perkuat penjualan di state dengan kontribusi besar**. California memberikan revenue tertinggi ($5,1 juta), jauh di atas state lainnya. Hal ini menunjukkan potensi pasar yang besar di wilayah tersebut. Strategi promosi dan distribusi di California sebaiknya terus diperkuat, sambil mengeksplorasi peluang pertumbuhan di state dengan kontribusi menengah seperti South Carolina, Florida, dan New York.
5. **Optimalkan Strategi Berdasarkan Metode Penjualan**. Penjualan melalui toko fisik (in-store) terbukti memberikan revenue terbesar, sedangkan online mencatat volume transaksi tertinggi. Perusahaan sebaiknya memaksimalkan potensi kedua metode ini dengan menjaga pengalaman belanja di toko fisik serta meningkatkan promosi digital untuk memperluas jangkauan pasar. Sementara itu, penjualan melalui outlet dapat difokuskan sebagai media rotasi stok dan program diskon tanpa mengganggu positioning produk utama.

