# Dashboard Single HTML — Vercel + GitHub + Google Spreadsheet

Versi ini menggabungkan **HTML, CSS, JavaScript, grafik, format Rupiah, dan tarikan Google Spreadsheet dalam satu file `index.html`**. Tidak ada folder `api`, `app.js`, atau `styles.css`.

## Isi folder

- `index.html` — seluruh website dan koneksi Spreadsheet.
- `spreadsheet-template.xlsx` — template yang diunggah ke Google Drive lalu dibuka sebagai Google Spreadsheet.
- `vercel.json` — konfigurasi opsional untuk URL bersih.

## Pengaturan permanen

Buka `index.html`, cari:

```js
const DASHBOARD_CONFIG = {
  spreadsheetId: "GANTI_ID_SPREADSHEET_DI_SINI",
```

Ganti dengan ID Spreadsheet, misalnya:

```js
spreadsheetId: "1AbCdEfGhIjKlMnOpQrStUvWxYz123456789",
```

ID berada di antara `/d/` dan `/edit` pada URL Google Spreadsheet.

## Pengaturan tanpa mengedit kode

Pada website, klik **Pengaturan Spreadsheet**, tempel URL atau ID, kemudian klik **Simpan & Muat Data**. Pengaturan ini hanya tersimpan pada browser/perangkat tersebut. Untuk konfigurasi yang berlaku bagi semua pengunjung, ubah `DASHBOARD_CONFIG` di GitHub.

## Google Spreadsheet

1. Upload `spreadsheet-template.xlsx` ke Google Drive.
2. Buka menggunakan Google Spreadsheet.
3. Jangan ubah nama tab: `SUMMARY`, `TREND`, `SALESPERSON`, `DEPARTMENT`, `ALERTS`.
4. Klik **Bagikan** → **Akses umum** → **Siapa saja yang memiliki link** → **Pelihat**.
5. Isi atau edit angka langsung di Spreadsheet. Dashboard membaca perubahan saat halaman dimuat ulang atau tombol refresh ditekan.

## Upload ke GitHub

1. Buat repository baru.
2. Upload `index.html` dan `vercel.json` ke halaman utama repository.
3. Commit perubahan.

## Deploy ke Vercel

1. Login Vercel.
2. Pilih **Add New → Project**.
3. Import repository GitHub.
4. Framework Preset dapat dibiarkan **Other**.
5. Tidak perlu Environment Variable.
6. Klik **Deploy**.

## Struktur header Spreadsheet

Jangan mengubah header pada baris pertama. Penambahan tanggal, store, sales person, department, dan alert dilakukan dengan menambah baris baru di tab yang sesuai.

## Catatan keamanan

Versi single HTML memakai data Spreadsheet yang dapat dilihat melalui link. Jangan menaruh data sensitif. Spreadsheet privat memerlukan OAuth atau backend, sehingga tidak cocok disimpan seluruhnya dalam satu HTML statis.
