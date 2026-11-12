# PROJECT MEMORY: PORTAL SEMAKAN PENYERTAAN MBPK KE PPI

Dokumen memori ini merekodkan semua spesifikasi, senibina data, logik sistem, dan ketetapan penting projek ini untuk rujukan penambahbaikan pada masa hadapan.

---

## 1. Maklumat Asas Projek
* **Nama Portal:** PORTAL SEMAKAN PENYERTAAN MBPK KE PPI
* **Pemilik Repositori:** MORRIS1971
* **Pautan Laman Web Rasmi (Live URL):** https://morris1971.github.io/portal-semakan-mbpk-ppi/
* **Pautan GitHub Repository:** https://github.com/MORRIS1971/portal-semakan-mbpk-ppi.git
* **Lokasi Tempatan Projek:** `C:\Users\morris.jitai\Desktop\PORTAL-SEMAKAN-MBPK-PPI`
* **Fail Utama:** `index.html`, `data_mbpk_ppki_tindakan_guru.csv`, `data_mbpk_separa_arkib.csv`, `PROJECT_MEMORY.md`, `README.md`

---

## 2. Peraturan & Ketetapan Pengguna (User Preferences & Operational Rules)
1. **Penyerahan Fail Siap:** 
   * Semua fail siap pengekodan **MESTI disalin/diserahkan terus ke Desktop pengguna** pada laluan:
     `C:\Users\morris.jitai\Desktop\PORTAL-SEMAKAN-MBPK-PPI`.
2. **Aliran Kemas Kini Auto-Sync (CI/CD):**
   * Setiap kali penambahbaikan dibuat:
     1. Kod dikemas kini pada Desktop.
     2. Lakukan `git add`, `git commit` dan `git push origin main`.
     3. GitHub Pages akan membina (*auto-deploy*) versi terkini dalam masa 30–60 saat.
     4. URL laman web kekal sama tanpa perlu muat naik manual.

---

## 3. Senibina & Struktur Data Enrolmen
* **Jumlah Enrolmen Asal:** 121 MBPK
* **Skop Semakan Guru (Murid PPKI Aktif):** 53 Murid
* **Murid Sedia Ada PPI (Arkib Murid Separa):** 68 Murid (Digugurkan daripada semakan justifikasi untuk mengelakkan bebanan guru dan kekeliruan data).

### Pecahan Data Mengikut Sekolah:
| Kod Sekolah | Nama Sekolah | Murid Disemak (PPKI) | Murid Separa (Arkib) |
| :--- | :--- | :---: | :---: |
| **YBB3311** | SK NANGA NGUNGUN | 3 | 5 |
| **YBB3323** | SK NANGA PEDAI | 7 | 5 |
| **YCB3301** | SK ST FRANCIS XAVIER | 16 | 9 |
| **YBB3320** | SK ULU RANAN | 20 | 15 |
| **YEB3301** | SMK DATUK HAJI ABDUL RAHMAN YAKUB | 1 | 9 |
| **YEA3302** | SMK KANOWIT | 6 | 25 |
| **JUMLAH** | | **53** | **68** |

---

## 4. Logik & Ciri-Ciri Utama Sistem

1. **Penyeragaman 4 Kad KPI & Penapis Sekolah (*Real-Time Sync*):**
   * Apabila pengguna memilih sekolah daripada *Dropdown*, 4 kad utama di bahagian atas (MBPK Disemak, Ada Justifikasi, Belum Ada Justifikasi, Arkib Murid Separa) serta bilangan pada butang penapis (Semua, Belum Diisi, Selesai, Berpindah) **wajib bertukar mengikut angka sekolah berkenaan secara automatik**.
2. **Auto-Reset ke Tab "Semua":**
   * Apabila sekolah bertukar, sistem secara automatik menetapkan paparan kepada tab "Semua" supaya senarai murid sentiasa kelihatan serta-merta.
3. **Pengurusan Justifikasi & Intervensi (Modal Pop-Up):**
   * Pilihan Justifikasi Standard:
     1. Umur Belum Melayakkan
     2. Tantrum / Emosi / Disiplin
     3. Ketidakupayaan Fizikal
     4. Pengurusan Diri Belum Dikuasai (Toilet/Kebersihan)
     5. Tahap Kognitif / 3M Belum Bersedia
     6. Gangguan Sensori / Hiperaktif Tinggi
     7. Masalah Komunikasi & Pertuturan Terhad
     8. Lain-lain Sebab (Nyatakan)
   * Perancangan Intervensi Pantas (RPI 2.0, Modifikasi Tingkah Laku, Terapi Sensori, Pemulihan 3M, Kokurikulum).
4. **Fungsi Kemas Kini Status & Padam Rekod:**
   * Guru boleh menukar status murid: `AKTIF BERSEKOLAH`, `BERPINDAH SEKOLAH`, `BERHENTI / TIDAK BERSEKOLAH`, `TAMAT PERSEKOLAHAN`.
   * Murid yang berpindah/berhenti diasingkan ke tab *Berpindah/Berhenti* supaya tidak mencacatkan peratus kesiapan sekolah.
   * Disediakan butang padam rekod pada jadual dan modal (lengkap dengan *confirmation prompt*).
5. **Fungsi Tambah MBPK Baharu (Pendaftaran Terkini):**
   * Butang hijau zamrud **"+ Tambah MBPK"** diletakkan di bar atas bersebelahan "Arkib Murid Separa".
   * Modal pendaftaran lengkap merangkumi semua atribut standard:
     * Sekolah (Dropdown automatik mengikut senarai 6 sekolah atau pra-pilih sekolah aktif)
     * Nama Penuh Murid
     * No. KP / No. MyKid
     * No. Kad OKU / JKM
     * Kategori Ketidakupayaan (Pembelajaran, Penglihatan, Pendengaran, Fizikal, Pertuturan, Pelbagai)
     * Tahap Persekolahan / Kelas
     * Jantina & Bangsa
     * Status Keberadaan Murid
   * Rekod baharu secara automatik diserap ke senarai semakan PPKI, dikemaskini dalam kad KPI, dan dimuat turun bersama dalam fail CSV.
6. **Pengurusan Arkib Separa:**
   * Modal khas untuk menyemak 68 murid sedia ada PPI Separa.
   * Menyokong kemas kini status perpindahan atau padam rekod.
7. **Eksport CSV Terkini:**
   * Muat turun laporan CSV lengkap dengan satu klik untuk pelaporan Unit Pendidikan Khas (UPK) ke PPD / JPN.
8. **Penyimpanan Selamat (*Safe Storage*):**
   * Menggunakan mod sandaran memori master data dan diselaraskan ke `localStorage` agar data guru tersimpan rapi tanpa risiko ranap (*crash*).

---

## 5. Panduan Tetapan GitHub Repository & GitHub Pages
* **Alamat Laman Web (Website):** `https://morris1971.github.io/portal-semakan-mbpk-ppi/`
* **Keterangan Repositori (Description):** `Portal Semakan Penyertaan Murid Berkeperluan Pendidikan Khas (MBPK) ke Program Pendidikan Inklusif (PPI)`
* **Tetapan GitHub Pages:**
  1. Pergi ke tab **Settings** > **Pages**
  2. Source: **Deploy from a branch**
  3. Branch: **main** / folder: `/(root)`
  4. Tekan **Save**.
