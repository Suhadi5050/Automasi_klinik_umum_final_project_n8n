# AI-Powered Clinic Triage & Patient Registration Automation (n8n)

Sistem otomatisasi pendaftaran dan triase pasien untuk klinik umum berbasis n8n, Google Forms/Sheets, Google Gemini AI, dan Telegram Bot. Proyek ini dirancang untuk menyederhanakan alur pendaftaran pasien, menganalisis tingkat urgensi secara otomatis, menghasilkan ringkasan medis untuk dokter, serta memberikan notifikasi instan kepada staf klinik.

---

## Fitur Utama

* **Pendaftaran Fleksibel:** Menggunakan ekosistem Google (Google Forms & Google Sheets) sebagai antarmuka pengumpulan data pasien yang mudah diakses.
* **Triase & Analisis AI Cerdas:** Memanfaatkan Google Gemini AI untuk mengkategorikan tingkat urgensi pasien secara otomatis ke dalam label:
  * `[DARURAT]`
  * `[SEDANG]`
  * `[RINGAN]`
* **Ringkasan Medis Otomatis:** AI menghasilkan ringkasan keluhan utama pasien yang terstruktur dan ramah dibaca oleh dokter umum.
* **Manajemen Nomor Antrean & Database:** Sinkronisasi otomatis data pasien ke dalam Google Sheets lengkap dengan penomoran antrean.
* **Notifikasi Instan Telegram:** Mengirimkan hasil analisis, tingkat urgensi, dan data pasien secara real-time ke bot klinik menggunakan format plain text yang bersih dari Markdown.

---

## Tech Stack

* **Workflow Engine:** n8n (Self-hosted / Cloud)
* **Data Collection & Storage:** Google Forms & Google Sheets
* **Artificial Intelligence:** Google Gemini AI (via LangChain / AI Agent node)
* **Notification Channel:** Telegram Bot API

---

## Arsitektur Alur Kerja (Workflow Architecture)

1. **Trigger:** Google Sheets Trigger memantau baris baru yang masuk secara otomatis saat pasien mengirimkan respons melalui Google Form.
2. **AI Processing:** Data pasien dikirim ke AI Agent yang ditenagai oleh Google Gemini Chat Model untuk dianalisis gejala dan tingkat urgensinya.
3. **Database Logging:** Data yang telah diproses otomatis tercatat rapi ke dalam Google Sheets sebagai database klinik.
4. **Notification:** Bot Telegram mengirimkan laporan lengkap kepada staf atau dokter yang bertugas secara instan.

---

## Struktur Data Spreadsheet (Google Sheets)

Pastikan Google Sheets penampung data memiliki kolom dengan urutan atau nama berikut agar sinkron dengan otomatisasi:
* `nomor_Urut_Pasien`
* `Nama_Pasien`
* `Umur_Pasien`
* `Nomor_Telepon/WhatsApp`
* `Keluhan_Utama/Gejala`
* `Tanggal_Kunjungan`

---

## Cara Menjalankan Proyek

1. **Setup Google Forms & Google Sheets:**
   * Buat Google Form untuk pendaftaran pasien.
   * Hubungkan respons Google Form ke Google Sheets melalui tab *Responses* di Google Form.
   * **Catatan Penting:** Pastikan akun Google yang digunakan untuk membuat Google Form, Google Sheets, dan yang dihubungkan ke kredensial n8n adalah **akun yang sama** agar izin akses (*permissions*) dan sinkronisasi data berjalan lancar tanpa kendala *unauthorized*.
2. **Clone atau Import Workflow ke n8n:**
   * Unduh file JSON workflow n8n dari repositori ini.
   * Buka n8n, klik menu titik tiga di sudut kanan atas, lalu pilih **Import from File**.
3. **Konfigurasi Kredensial:**
   * Hubungkan kredensial Google Sheets untuk Trigger dan Tool.
   * Hubungkan kredensial Google Gemini API pada node Chat Model.
   * Hubungkan kredensial Telegram Bot API pada node Telegram.
4. **Atur ID Spreadsheet:**
   * Sesuaikan `Document ID` pada node Google Sheets dengan ID spreadsheet penampung respons Google Form milikmu.
5. **Aktivasi Workflow:**
   * Ubah status workflow di n8n menjadi **Active**, lalu coba isi Google Form pendaftaran untuk melakukan pengujian.

---

## Dokumentasi / Preview

*(Kamu dapat menyertakan tangkapan layar atau screenshot tampilan workflow n8n maupun hasil chat Telegram di bagian ini)*
* **n8n Workflow Preview:** Menampilkan Google Sheets Trigger, AI Agent, dan Telegram Node.
* **Telegram Notification:** Hasil notifikasi instan berlabel urgensi.

---
*Dibuat sebagai Final Project Automasi Sistem Klinik menggunakan n8n.*