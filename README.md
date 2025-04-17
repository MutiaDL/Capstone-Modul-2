# Capstone-Modul-2

## 1. Pendahuluan
SaaS (Software as a Service) merupakan model bisnis di mana perangkat lunak disediakan sebagai layanan melalui internet, bukan dijual sebagai produk satuan. Pengguna umumnya membayar biaya langganan secara berkala, baik bulanan maupun tahunan, untuk mengakses layanan dan fitur perangkat lunak yang dibutuhkan. Contoh layanan SaaS populer antara lain Dropbox, Zoom, Google Workspace, dan Salesforce. Model bisnis SaaS menawarkan fleksibilitas dan efisiensi tinggi, baik bagi penyedia layanan maupun pengguna. Oleh karena itu, semakin banyak perusahaan, khususnya dalam skala B2B (Business to Business), yang mengadopsi model ini. Dalam kondisi persaingan pasar yang ketat, penting bagi perusahaan untuk memahami perilaku pelanggan dan tren penjualan agar dapat menjaga profitabilitas dan pertumbuhan bisnis.

Salah satu strategi yang umum digunakan untuk meningkatkan penjualan adalah pemberian diskon. Diskon dianggap mampu mendorong pembelian dan membangun loyalitas pelanggan. Namun, tidak semua program diskon berdampak positif terhadap keuntungan. Diskon besar yang tidak terarah justru dapat menurunkan margin keuntungan atau bahkan menyebabkan kerugian. Oleh karena itu, evaluasi berbasis data sangat penting. Selain itu, memahami produk mana yang paling berkontribusi terhadap profit sangatlah krusial. Tidak semua produk dengan volume penjualan tinggi otomatis menguntungkan, terutama jika penjualannya tergantung pada diskon besar. Dengan memahami hal ini, perusahaan dapat lebih fokus pada produk yang benar-benar menguntungkan dan menghindari promosi yang merugikan.

## 2. Rumusan Masalah dan Tujuan
Rumusan Masalah:
1. Bagaimana pengaruh diskon terhadap jumlah penjualan dan profit? Sejauh mana strategi diskon yang diterapkan efektif meningkatkan profitabilitas?
2. Produk apa saja yang memberikan kontribusi profit terbesar dan layak diprioritaskan dalam strategi penjualan?

Tujuan:
1. Menilai efektivitas strategi diskon dan menghindari praktik promosi yang merugikan.
2. Mengidentifikasi produk-produk yang layak diprioritaskan dalam strategi penjualan.

## 3. Data
Dataset yang digunakan adalah AWS SaaS Sales Dataset dari Kaggle:https://www.kaggle.com/datasets/nnthanh101/aws-saas-sales. Dataset terdiri dari 19 kolom, di mana setiap baris merepresentasikan satu produk dalam suatu transaksi. Beberapa kolom utama:
- Order ID: ID unik tiap transaksi
- Order Date: Tanggal pemesanan
- Customer: Nama perusahaan pembeli
- Segment, Industry: Kategori pelanggan
- Product: Nama produk SaaS
- Sales, Discount, Profit: Nilai penjualan, diskon yang diberikan, dan keuntungan
- Region, Country: Lokasi geografis pemesanan

## 4. Data Understanding & Cleaning
- Total 9994 baris data  dengan 19 kolom.
- Menghapus kolom tidak relevan seperti Row ID, Date Key, Contact Name, City, Subregion, dan License.
- Cek Missing Value.
- Mengubah tipe data untuk kolom Order Date menjadi datetime dan Customer ID menjadi object.
- Menghapus duplikat - terdapat 1 baris duplikat (0.01%).
- Cek Rentang waktu data transaksi - Hasilnya data transaksi berkisar dari Januari 2020 hingga Desember 2023.
  
## 5.Hasil Analisis
Temuan Utama:
- 48% transaksi tanpa diskon → menghasilkan penjualan dan profit terbesar (sales: $1.09 juta, margin: 29.5%).
- Diskon 20% paling sering diberikan (36.6%) → kemungkinan strategi utama.
- Diskon besar (70%-80%) meski jarang, menimbulkan kerugian besar dan margin negatif.
- Diskon aneh (32%, 45%, dll) sangat jarang → bisa jadi bug sistem atau promo khusus.
- Segmentasi Diskon - Untuk mempermudah analisis, diskon dikelompokkan sebagai berikut:

1.Tanpa Diskon (0%)
2. Diskon Ringan (10%-20%)
3. Diskon Sedang (30%-50%)
4. Diskon Tinggi (>50%)
- Strategi tanpa diskon atau diskon ringan (≤ 20%) terbukti paling sehat secara profitabilitas.
- Diskon besar (>30%) cenderung menyebabkan kerugian, bahkan jika volume penjualan meningkat.
- Margin keuntungan menurun drastis seiring besarnya diskon: Tanpa Diskon: margin +29.5%, Diskon Tinggi: margin -119.2%
- Rata-rata profit per transaksi juga paling tinggi pada produk tanpa diskon.
- Diskon tinggi bisa merusak persepsi nilai produk dan margin keuntungan.
- Produk dengan permintaan stabil tetap memiliki transaksi tinggi meski tanpa diskon.
- Evaluasi strategi diskon perlu mempertimbangkan apakah diskon tinggi hanya untuk produk deadstock atau event promosi terbatas.
- Musim penjualan meningkat terlihat pada pertengahan hingga akhir tahun, diduga karena pola belanja tahunan perusahaan.
- Untuk mengevaluasi kontribusi profit produk secara menyeluruh, produk diklasifikasikan ke dalam empat segmen berdasarkan total profit, margin, dan rata-rata profit per transaksi:

1. Star
Produk dengan total profit, margin, dan rata-rata profit per transaksi tinggi.Contoh: Alchemy → profit sangat tinggi, margin bagus, kontribusi besar terhadap keuntungan perusahaan → layak diprioritaskan.
2. Volume Driver
Total profit tinggi, namun margin dan rata-rata profit sedang.Contoh: Data Smasher, Site Analytics, FinanceHub, Marketing Suite - Gold, Support → fokus pada volume penjualan dengan margin per transaksi lebih rendah, tapi tetap menguntungkan.
3. Loss Maker
Total profit dan margin rendah atau negatif. Contoh: Marketing Suite, Big Ol Database, SaaS Connector Pack - Gold, ContactMatcher → meski volume penjualan tinggi, tidak menguntungkan dan perlu evaluasi strategi harga atau pemasaran.
4. Premium Niche
Seharusnya produk dengan profit per transaksi tinggi namun total profit rendah. Tidak ditemukan dalam dataset karena mayoritas produk memiliki margin sedang atau rendah.

## 6. Kesimpulan
Efektivitas Strategi Diskon:
- Transaksi tanpa diskon tetap dominan dan menguntungkan → kontribusi profit dan margin tertinggi.
- Diskon ringan (10–20%) masih efektif → menarik pembeli tanpa merusak profit.
- Diskon sedang (30–50%) mulai merugikan → penjualan tidak cukup menutup potongan harga.
- Diskon tinggi (>50%) sangat merugikan → margin negatif, profit anjlok.
- Diskon besar digunakan terlalu sering → menurunkan persepsi nilai produk dan profit jangka panjang.
- Efektivitas diskon berbeda per produk → Alchemy tetap untung saat diskon, Marketing Suite - Gold tetap rugi meski diskon kecil.
- Prioritas Produk untuk Strategi Penjualan:
- Produk paling menguntungkan: Alchemy, Site Analytics, Data Smasher – profit tinggi, layak diprioritaskan.
- Performa stabil: Marketing Suite - Gold, FinanceHub, Support – profit konsisten dari volume besar.
- Produk merugi: Marketing Suite – profit negatif, margin rendah, diskon besar-besaran jadi penyebab utama.
- Produk setipe, performa berbeda: Marketing Suite - Gold lebih sehat dari versi biasa.

## 7. Rekomendasi
Strategi diskon ke depan:
- Prioritaskan penjualan tanpa diskon atau dengan diskon ringan (≤20%). Gunakan diskon hanya sebagai pemanis, bukan senjata utama. Produk terbukti tetap laku dan menguntungkan tanpa perlu potongan harga besar.
- Evaluasi dan batasi penggunaan diskon sedang–tinggi (>30%). Hanya gunakan diskon besar untuk tujuan khusus seperti clearance atau penjualan produk yang sudah lama tidak laku, dengan kontrol ketat pada durasi dan target produk.
- Segmentasikan strategi diskon berdasarkan produk. Implementasikan pendekatan berbasis produk. Misalnya, diskon boleh diterapkan untuk produk seperti Alchemy, tapi harus dihindari pada produk seperti Marketing Suite - Gold yang tidak sensitif terhadap diskon.
- Perkuat nilai produk untuk mengurangi ketergantungan pada diskon. Fokus pada branding, kualitas, atau layanan tambahan yang membuat konsumen tetap tertarik walau tanpa diskon. Ini bisa menjaga margin tetap sehat.
- Lakukan monitoring rutin. Gunakan data time series untuk mengidentifikasi momen efektif (misalnya, seasonal campaigns).

Strategi untuk menentukan produk mana yang diprioritaskan dalam penjualan:
- Fokus penjualan pada produk Star dan Volume Driver. Prioritaskan Alchemy untuk strategi high-margin premium. 
- Evaluasi dan restrukturisasi produk Loss Maker. Marketing produk perlu di-review secara menyeluruh dengan mengurangi atau menghentikan diskon ekstrem, meninjau kembali fitur dan posisinya di pasar (bisa jadi perlu relaunch atau bundling baru).
- Dorong versi premium yang terbukti efektif. Marketing Suite - Gold lebih menjanjikan dan lebih stabil. Pertimbangkan untuk mendorong pelanggan ke versi ini lewat upgrade path, promosi terbatas, atau penyesuaian fitur/value.
- Optimalkan strategi diskon. Hindari penggunaan diskon besar tanpa analisis dampak profit. Perlu dikembangkan model promosi berbasis profitabilitas, bukan sekadar peningkatan volume.
