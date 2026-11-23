# PROJECT MEMORY: PORTAL SEMAKAN PENYERTAAN MBPK KE PPI

Dokumen rujukan pembangunan portal. Dikemas kini berdasarkan data November 2026.

## 1. Maklumat Projek
- Nama: PORTAL SEMAKAN PENYERTAAN MBPK KE PPI
- Repositori: https://github.com/MORRIS1971/portal-semakan-mbpk-ppi
- Live URL: https://morris1971.github.io/portal-semakan-mbpk-ppi/
- Fail aplikasi: `index.html`

## 2. Sumber Data Diselaraskan — November 2026
Jumlah induk: **155 MBPK** di 18 sekolah.
- PPKI / tindakan guru: **41**
- PPI Separa: **84**
- PPI Penuh: **30**
- Arkib PPI (Separa + Penuh): **114**

## 3. Fail Data Kanonik
1. `MASTER_MBPK_PPI_KANOWIT_NOV2026.csv` — set induk penuh 155 rekod.
2. `data_mbpk_ppki_tindakan_guru.csv` — 41 rekod PPKI.
3. `data_mbpk_separa_arkib.csv` — 114 rekod PPI (84 Separa dan 30 Penuh).

Ketiga-tiga fail CSV menggunakan set medan yang sama: BIL, KOD_SEKOLAH, NAMA_SEKOLAH, NAMA_MBPK, ID_PELAJAR, NO_OKU, KATEGORI_KETIDAKUPAYAAN, JANTINA, UMUR, PROGRAM_KATEGORI, PERINGKAT_PERSEKOLAHAN, TAHUN_TINGKATAN, ALIRAN_KELAS, STATUS_PERSEKOLAHAN, JUSTIFIKASI_TIDAK_DIINKLUSIFKAN, CATATAN, PERANCANGAN_INTERVENSI.

## 4. Peraturan Pembangunan Seterusnya
- Jadikan master CSV sebagai rujukan jumlah dan rekod keseluruhan.
- Modul tindakan guru membaca dataset PPKI 41 rekod.
- Modul arkib membaca dataset PPI 114 rekod dan membezakan PENUH/SEPARA melalui PROGRAM_KATEGORI atau STATUS_PERSEKOLAHAN.
- Jangan menganggap semua 155 rekod sebagai senarai tindakan guru.
- Kekalkan data asal dan medan kosong; jangan mereka maklumat yang tiada.
- Kekalkan fungsi sedia ada dalam `index.html` semasa penambahbaikan.
- Sebarang kemas kini data hendaklah disahkan melalui kiraan rekod, ID_PELAJAR unik dan padanan kategori.

## 5. Nota Pelaksanaan
Data CSV di repositori telah diselaraskan dengan data terbenam dalam `index.html`. Fail master gabungan disediakan sebagai sumber rujukan untuk pembangunan modul, penapis, statistik dan eksport pada fasa seterusnya.
