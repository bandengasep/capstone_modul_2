## Background

Amazon Web Services (AWS) adalah perusahan teknologi berbasis *cloud* yang menyediakan berbagai macam solusi teknologi untuk klien perusahaan-perusahaan internasional (*Business-to-Business*/B2B). Bermula dari inisiatif perusahaan Amazon.com untuk menyediakan layanan penyimpanan berbasis internet di tahun 2006 dengan layanan *Simple Storage Service* (S3), AWS telah bertumbuh untuk menyediakan layanan-layanan dari *data center* yang tersebar di seluruh penjuru dunia ([AWS, 2024](https://aws.amazon.com/about-aws/our-origins/)). 

Per tahun 2024, AWS telah menjadi ***market leader*** dengan persentase pasar internasional sebesar **31%**) sebagai penyedia layanan infrastruktur *cloud* ([Statista, 2024](https://www.statista.com/chart/18819/worldwide-market-share-of-leading-cloud-infrastructure-service-providers/)). Pada saat bersamaan, *run rate* AWS di tahun 2024 adalah **$110 milyar**, meningkat **19%** secara *Year-on-Year* didorong oleh layanan berbasis *Artificial Intelligence* (AI) seperti AWS *Bedrock* ([Yahoo Finance, 2024](https://finance.yahoo.com/news/amazon-rises-45-6-2024-120400789.html)).

Dengan klien yang tersebar di seluruh penjuru dunia dan jumlah produk yang mencapai ratusan jenis, maka perlu dilakukan analisa untuk mengetahui performa finansial secara wilayah internasional untuk mengetahui wilayah-wilayah yang memerlukan perhatian khusus.  

## Pernyataan Masalah
Perusahaan AWS ingin mengetahui tren *profit margin* setiap transaksi dari tahun 2020 hingga 2023. Perusahaan juga ingin mengetahui apakah terdapat korelasi antara diskon dan *profit* yang dihasilkan sepanjang periode tersebut serta penjabaran *profit margin* per regional. 

Sebagai seorang *data analyst*, maka kita akan menganalisa dataset `SaaS_Sales` yang telah dikumpulkan oleh perusahaan dengan formulasi pernyataan masalah berikut:

1. Bagaimana tren *profit margin* perusahaan dari tahun 2020 hingga 2023?
2. Apakah diskon secara signifikan mempengaruhi *profit margin* perusahaan?
   - Apakah terdapat wilayah/*region* dan sub-wilayah/*subregion* yang memiliki diskon besar dengan marjin laba bersih/*profit margin* yang negatif?
3. Segmen dan produk apa saja yang berkontribusi signifikan terhadap sub-wilayah dengan *profit margin* negatif dan diskon terbesar?

## Data
Dataset `SaaS_Sales.csv` berisi informasi terkait data-data transaksi seperti negara asal klien, segmen klien, dan jenis produk yang dijual. Terdapat 20 kolom, yakni:

| No | Nama Atribut     | Deskripsi                                                                 |
|----|------------------|--------------------------------------------------------------------------|
| 1  | `Row ID`          | Pengidentifikasi unik untuk setiap transaksi.                            |
| 2  | `Order ID`         | Pengidentifikasi unik untuk setiap pesanan.                              |
| 3  | `Order Date`       | Tanggal ketika pesanan dilakukan.                                        |
| 4  | `Date Key`         | Representasi numerik dari tanggal pesanan (YYYYMMDD).                    |
| 5  | `Contact Name`     | Nama orang yang melakukan pesanan.                                       |
| 6  | `Country`          | Negara tempat pesanan dilakukan.                                         |
| 7  | `City`             | Kota tempat pesanan dilakukan.                                           |
| 8  | `Region`           | Wilayah tempat pesanan dilakukan.                                        |
| 9  | `Subregion`        | Subwilayah tempat pesanan dilakukan.                                     |
| 10 | `Customer`        | Nama perusahaan yang melakukan pesanan.                                 |
| 11 | `Customer ID`      | Pengidentifikasi unik untuk setiap pelanggan.                            |
| 13 | `Industry`         | Industri tempat pelanggan berada.                                        |
| 14 | `Segment`          | Segmen pelanggan (SMB, Strategis, Perusahaan, dll.).                    |
| 15 | `Product`          | Produk yang dipesan.                                                    |
| 16 | `License`          | Kunci lisensi untuk produk.                                              |
| 17 | `Sales`            | Total nilai penjualan untuk transaksi.                                   |
| 18 | `Quantity`         | Jumlah total barang dalam transaksi.                                     |
| 19 | `Discount`         | Diskon yang diterapkan pada transaksi.                                   |
| 20 | `Profit`           | Keuntungan dari transaksi.                                              |

## Kesimpulan
Berdasarkan visualisasi dan uji tes statistik yang telah dilakukan, maka dapat disimpulkan bahwa terdapat korelasi negatif yang cukup signifikan antara diskon dengan marjin laba bersih. 

Kedua sub-wilayah dengan diskon terbesar dan marjin laba bersih terbesar adalah JAPN dan ANZ, sehingga perlu dilakukan evaluasi ulang terhadap strategi marketing dan diskon untuk kedua sub-wilayah tersebut.

### Ringkasan Wawasan
1. **Tren marjin laba bersih**: tidak terdapat tren yang dapat diobservasi secara langsung dari pergerakan marjin laba bersih dari tahun 2020 hingga 2023
2. **Dampak diskon terhadap marjin laba bersih**: berdasarkan visualisasi dan uji tes statistik, terdapat korelasi negatif yang cukup signifikan antara diskon dan laba bersih. Dapat disimpulkan bahwa semakin besar diskon yang diberikan kepada klien, maka semakin besar pula kerugian yang diderita oleh perusahaan AWS
3. **Wilayah dan Sub-Wilayah dengan diskon tertinggi dan marjin laba bersih terendah**: berdasarkan visulasi garis regresi dan uji tes statistik non-parametrik $Mann-Whitney\ U$, dapat disimpulkan bahwa wilayah **APJ** dan sub-wilayah **JAPN** dan **ANZ** memiliki diskon tertinggi dengan marjin laba bersih terendah
4. **Produk dan Segmentasi Kustomer di Sub-Wilayah JAPN dan ANZ**:
    - Berdasarkan diagram batang dan garis gabungan, dapat disimpulkan bahwa produk dengan laba bersih tertinggi seperti SaaS Connector Pack - Gold memiliki diskon terendah; sementara produk dengan diskon tinggi seperti Contact Matcher mencatatkan marjin laba bersih terendah.
    - Segmen SMB (*Small-Medium-Business*) memiliki pangsa tertinggi di sub-wilayah JAPN dan ANZ
    - Perusahaan yang mencatatkan *median* marjin laba bersih terbesar di sub-wilayah JAPN dan ANZ adalah:
        -  *Nissan Motor* untuk segmen *Enterprise*
        -  *Verizon Communications* untuk segmen SMB
        -  *Johnson & Johnson* untuk segmen *Strategic*
    - Perusahaan yang mencatatkan *median* marjin laba bersih terendah di sub-wilayah JAPN dan ANZ adalah:
            -  *Samsung Electronics* untuk segmen *Enterprise*
            -  *Glencore* untuk segmen SMB
            -  *Target* untuk segmen *Strategic*

### Rekomendasi
1. ***Customer Engagement* strategis**: Fokuskan upaya perusahaan untuk optimalisasi penjualan terhadap pelanggan-pelanggan utama dengan marjin laba bersih yang tinggi agar strategi *customer engagement* dapat dieksekusikan lebih baik untuk meningkatkan keuntungan perusahaan.

2. **Eksekusi *Cost Benefit Analysis* & *Pricing Strategy***: Lakukan evaluasi menyeluruh terhadap sub-wilayah JAPN dan ANZ, serta wilayah APJ untuk penetapan harga yang sesuai dengan ekspektasi pelanggan dan kondisi pasar.

3. **Optimasi Strategi Diskon & Inisiatif Penjualan**: Cari keseimbangan antara diskon dan margin keuntungan, serta formulasikan strategi *marketing* yang dapat meningkatkan laba bersih yang tidak memakai peningkatan diskon.

## Tableau Dashboard
Visualisasi Tableau bisa dilihat di [link ini](https://public.tableau.com/views/dashboard_saas_dataset/awsdashboard?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
