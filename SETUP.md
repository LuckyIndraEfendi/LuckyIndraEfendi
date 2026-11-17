# Memasang profil

Profil ini menggabungkan Skill Icons, Metrics, dan GitHub Stats. Ikon dan kartu statistik mengikuti tema terang atau gelap GitHub, dengan aksen biru yang selaras.

1. Simpan README.md, folder assets, github-metrics.svg, dan folder .github/workflows di repository profil publik LuckyIndraEfendi/LuckyIndraEfendi.
2. Commit dan push perubahan agar tampil pada profil GitHub. Tidak perlu deployment atau GitHub Pages.
3. Untuk preview lokal, buka README.md di VS Code lalu tekan Ctrl+Shift+V. Gambar lokal harus tersedia di path yang dirujuk README.
4. Daftar teknologi dapat disunting di bagian Technologies & tools beserta parameter ikon yang bersangkutan.

## Widget yang dipasang

| Widget | Isi | Sumber gambar |
| --- | --- | --- |
| [Skill Icons](https://github.com/tandpfun/skill-icons) | Bahasa, framework, database, cloud, dan tools | skillicons.dev, dengan varian terang dan gelap |
| [GitHub Stats](https://github.com/jstrieb/github-stats) | Kartu ringkasan kontribusi dan penggunaan bahasa | assets/stats/overview.svg dan assets/stats/languages.svg |
| [Metrics](https://github.com/lowlighter/metrics) | Detail aktivitas, komunitas, repository, dan bahasa | github-metrics.svg |

GitHub Stats tampil berdampingan di atas Metrics jika ruang mencukupi. Semua gambar memiliki teks alternatif. Kartu streak tidak digunakan.

## Pembaruan Metrics

Workflow: .github/workflows/metrics.yml, bernama **Update profile metrics**.

1. Gunakan secret repository METRICS_TOKEN yang sudah dipasang untuk membaca statistik akun LuckyIndraEfendi.
2. Untuk memperbarui sekarang, buka Actions → Update profile metrics → Run workflow.
3. Workflow menulis github-metrics.svg ke repository memakai GITHUB_TOKEN. Bagian GitHub activity di README sudah aktif.

Jadwal: sekitar pukul 06.00 WIB setiap hari. CSS di workflow menyesuaikan warna teks dengan tema terang atau gelap.

Dokumentasi: https://github.com/lowlighter/metrics/blob/master/.github/readme/partials/documentation/setup/action.md

## Pembaruan GitHub Stats

Workflow: .github/workflows/github-stats.yml, bernama **Update profile stats**.

1. Push workflow baru ke branch utama. Workflow berjalan saat file workflow ini berubah, dapat dijalankan manual lewat Actions, dan dijadwalkan sekitar pukul 06.20 WIB setiap hari.
2. Workflow menggunakan STATS_TOKEN jika tersedia; jika tidak, menggunakan METRICS_TOKEN yang sudah ada. Token tersebut harus milik LuckyIndraEfendi karena generator membaca akun pemilik token.
3. Bila token yang ada tidak memiliki izin yang diperlukan, buat personal access token sesuai dokumentasi GitHub Stats dan simpan sebagai secret STATS_TOKEN. Izin user:email membantu atribusi perubahan baris; tanpa izin ini generator memakai alamat noreply dan hasilnya bisa kurang lengkap. Dokumentasi upstream menjelaskan izin read:user, user:email, serta repo untuk akses repository privat.
4. Workflow mengunduh generator resmi versi 2.0.1, memverifikasi SHA-256, dan menghasilkan overview.svg serta languages.svg di assets/stats. Opsi --exclude-private mengeluarkan repository privat dari agregasi kartu repository dan bahasa.
5. GITHUB_TOKEN melakukan commit dan push kedua kartu ke branch utama. Kedua workflow menggunakan antrean yang sama agar pembaruan tidak berjalan bersamaan.

Tidak perlu membuat repository github-stats terpisah. Generator dipasang langsung dalam workflow repository profil ini. Statistik berasal dari GitHub API; keterbatasan hitungan dijelaskan di dokumentasi upstream.

Dokumentasi: https://github.com/jstrieb/github-stats

## Preview dan sinkronisasi

Workflow di GitHub memperbarui file di repository remote. Untuk melihat pembaruan itu secara lokal, sinkronkan perubahan dari GitHub setelah menyimpan pekerjaan lokal. Preview lokal menampilkan snapshot terakhir yang tersedia; ikon memerlukan koneksi internet.

GitHub dapat menunda workflow terjadwal. Jika suatu run gagal, gambar hasil run terakhir tetap dipakai.
