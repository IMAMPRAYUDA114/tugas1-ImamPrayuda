# Dataset CommonLingua-Train

## Informasi Dataset

| Item | Keterangan |
|---|---|
| Nama | `CommonLingua-Train` |
| Sumber | [Hugging Face](https://huggingface.co/datasets/PleIAs/CommonLingua-Train) |
| Lisensi | Per-source (lisensi berbeda berdasarkan sumber data) |
| Format | Parquet |
| Jumlah file | 2 file utama: `train.parquet` dan `val.parquet` |
| Jumlah baris | 2.755.443 baris berdasarkan metadata dataset: 2.482.568 data train dan 272.875 data validasi |
| Ukuran | Sekitar 1,2 GB berdasarkan halaman repository Hugging Face |
| Periode data | Bervariasi berdasarkan sumber data; tidak tersedia satu rentang tanggal yang berlaku untuk seluruh dataset |
| Unit analisis | Satu paragraf teks beserta label bahasa dan metadata sumber |

Dataset ini berisi teks dari 334 bahasa yang dikumpulkan dari Wikipedia dan berbagai korpus terbuka lainnya. Dataset dikembangkan untuk tugas identifikasi bahasa (*language identification*) dalam pemrosesan bahasa alami (*Natural Language Processing* atau NLP).

Dataset memiliki beberapa kolom utama:

- `text`: isi paragraf teks.
- `lang`: label bahasa menggunakan kode ISO 639-3.
- `source`: sumber asal teks.
- `identifier`: identitas atau URL sumber data jika tersedia.
- `title`: judul dokumen jika tersedia.
- `collection`: nama koleksi atau subkoleksi.
- `license`: informasi lisensi setiap rekaman.
- `open_type`: jenis keterbukaan atau lisensi data.
- `creator`: nama pembuat atau organisasi jika tersedia.
- `date`: tanggal publikasi atau ekstraksi jika tersedia.

Struktur kolom dapat berbeda sesuai versi file yang digunakan. Informasi lisensi, pembuat, dan identitas sumber perlu dipertahankan apabila data akan didistribusikan kembali.

## Lokasi Penyimpanan

Seluruh file data mentah disimpan tanpa modifikasi di:

```text
data/raw/commonlingua-train/
├── train.parquet
└── val.parquet
```

Folder tersebut sengaja diabaikan oleh Git agar file dataset berukuran besar tidak ikut diunggah ke repository proyek. Cache dari proses pengunduhan tidak diperlukan untuk menjalankan analisis apabila file mentah sudah tersedia secara lokal.

Hasil pembersihan dan transformasi data disimpan secara terpisah di direktori:

```text
data/processed/
```

## Cara Memperoleh Data

1. Buka repository dataset [PleIAs/CommonLingua-Train](https://huggingface.co/datasets/PleIAs/CommonLingua-Train).
2. Buka bagian [Files and versions](https://huggingface.co/datasets/PleIAs/CommonLingua-Train/tree/main).
3. Unduh file `train.parquet` dan `val.parquet`.
4. Simpan kedua file ke folder `data/raw/commonlingua-train/`.
5. Jangan mengubah file mentah. Apabila diperlukan proses pembersihan atau transformasi, simpan hasilnya di `data/processed/`.
6. Catat checksum setiap file untuk memeriksa integritas data.

## Penggunaan pada Notebook

Notebook `notebooks/01_data_profiling.ipynb` digunakan untuk melakukan pemeriksaan awal dataset, seperti jumlah baris, nama kolom, tipe data, nilai kosong, duplikasi, distribusi label bahasa, dan ukuran file.

Untuk membaca data Parquet dalam jumlah besar, pemrosesan dapat dilakukan menggunakan Polars dengan lazy evaluation melalui `pl.scan_parquet()`, sehingga data tidak harus langsung dimuat seluruhnya ke memori.

## Kesesuaian dengan Ketentuan Tugas

Berdasarkan metadata repository, dataset ini memiliki lebih dari satu juta rekaman dan ukuran sekitar 1,2 GB. Dengan demikian, dataset memenuhi batas ukuran dan jumlah baris apabila ketentuan tugas menggunakan ambang minimal 500 MB atau satu juta baris.
