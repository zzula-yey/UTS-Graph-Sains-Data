# UTS-Graph-Sains-Data
Nama : Nazula Sinta Wati
NIM  : 23031554105

Ringkasan

Interaksi pengunjung e-commerce (view, addtocart, transaction) dimodelkan sebagai graf bipartit berarah di Neo4j:

(:Visitor {visitorId}) -[:VIEWED | :ADDED_TO_CART | :BOUGHT {timestamp, period, transactionId}]-> (:Item {itemId})

Dari graf periode training (P1) dibangun matriks interaksi (VSM), proyeksi User-User dan Item-Item, perhitungan cosine similarity, lalu rekomendasi KNN yang dievaluasi pada periode testing (P2) dengan Hit@5 dan NDCG@5.

Struktur Repositori
.
├── uts.ipynb                      # notebook utama (dokumentasi, kode, output)
├── requirements.txt               # dependensi Python
├── data/
│   ├── events_train_P1.csv        # hasil filter periode P1 (training)
│   └── events_test_P2.csv         # hasil filter periode P2 (testing)
└── hasil/                         # tabel hasil analisis (CSV)
Sumber Data

RetailRocket E-commerce Dataset (Roman Zykov), berkas events.csv: https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset

Data mentah (events.csv, item_properties_*.csv, category_tree.csv) tidak diunggah karena ukurannya besar. Unduh dari tautan di atas dan letakkan di folder data/ untuk mereproduksi hasil.

Periode yang Dipilih
Fold	Rentang (UTC)	Timestamp awal (ms)	Timestamp akhir (ms)
P1 (training)	2015-05-15 s.d. 2015-06-15	1431648000000	1434412799000
P2 (testing)	2015-08-15 s.d. 2015-09-15	1439596800000	1442361599000
