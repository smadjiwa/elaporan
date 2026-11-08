# e-Laporan Harian SMadJiwa — Portal Bersepadu

## Kandungan
- `index.html` — portal utama, header sekolah, tab Guru/Warden
- `guru.html` — borang Guru Bertugas asal yang dibekalkan
- `rekod-guru.html` — halaman Rekod Pelaporan Guru asal yang dibekalkan

## Terbitkan di GitHub Pages
1. Cipta repository GitHub, contohnya `elaporan-smadjiwa`.
2. Muat naik ketiga-tiga fail ini ke root repository.
3. Pergi ke Settings → Pages.
4. Pilih Deploy from a branch → `main` → `/ (root)` → Save.
5. Buka URL GitHub Pages yang diberikan.

## Nota integrasi Warden
Portal memuatkan dua URL Google Apps Script Warden dalam iframe. Jika iframe ditolak,
ubah fungsi `doGet()` dalam kedua-dua projek GAS Warden supaya output membenarkan iframe,
contohnya:
`return HtmlService.createHtmlOutputFromFile('Index').setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);`
Gunakan nama fail HTML sebenar projek berkenaan, dan deploy versi baharu. Jika projek menggunakan
`createTemplateFromFile(...).evaluate()`, panggil `setXFrameOptionsMode(...)` pada output evaluate.

`ALLOWALL` membenarkan mana-mana laman membingkaikan aplikasi. Gunakan hanya jika sesuai dengan
polisi keselamatan sekolah dan pastikan aplikasi mempunyai kawalan akses yang betul.

## Perkara penting
- Fail Guru asal disalin tanpa mengubah logik borang dan URL backend.
- Rekod Guru menggunakan URL Apps Script asal yang sudah tertanam dalam fail asal.
- Dashboard Warden kekal menggunakan URL yang diberikan.
- Ini ialah integrasi frontend; tiada perubahan dibuat pada spreadsheet atau deployment backend.


## Pautan Warden yang digunakan
- Borang Warden: `https://script.google.com/a/macros/moe-dl.edu.my/s/AKfycbxZJWRgYNCdohjAdFySnURZfk73dR9XzC_IRt2FKAHWuPOYiIO273Ni01OcECBckPJK/exec`
- Dashboard Warden: `https://script.google.com/a/macros/moe-dl.edu.my/s/AKfycbxQZxZ45iAHdpqreZ7opIqaVCH6tunNyPM_UAtxLZKJBBwwu2rTTFS6k7vEzOjbwizroA/exec?v=dashboard`

Pautan terus disediakan di bawah iframe sebagai pilihan jika pelayar atau Apps Script menyekat paparan terbenam.
