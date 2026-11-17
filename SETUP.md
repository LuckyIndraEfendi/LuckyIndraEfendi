# Memasang profil

1. Salin README.md ke repository profil publik LuckyIndraEfendi/LuckyIndraEfendi. README utama langsung dapat dipakai tanpa token atau workflow.
2. Cek kembali akun LinkedIn dan X milikmu. Keduanya dipertahankan dari teks asli, bukan dinyatakan terverifikasi. Alamat email juga dipertahankan dari teks asli.
3. Daftar teknologi adalah ringkasan dari konteks pekerjaan dan proyek; hapus yang tidak ingin ditampilkan. Go dan TypeScript sengaja ditulis sebagai teknologi yang sedang dieksplorasi.

## Statistik opsional: lowlighter/metrics

Dokumentasi: https://github.com/lowlighter/metrics
Pengaturan: https://github.com/lowlighter/metrics/blob/master/.github/readme/partials/documentation/setup/action.md

1. Salin .github/workflows/metrics.yml ke path yang sama dalam repository profil. Folder .github tersembunyi pada sebagian aplikasi ekstraksi; pastikan ikut tersalin.
2. Buat personal access token untuk pembacaan statistik publik mengikuti dokumentasi Metrics. Untuk data publik, jangan berikan scope repo, read:org, atau read:user yang tidak diperlukan. Akun/organisasi tertentu mungkin menerapkan batasan token tambahan.
3. Di repository profil buka Settings → Secrets and variables → Actions → New repository secret, beri nama METRICS_TOKEN. Tempel token di kolom secret, bukan di README atau YAML.
4. Buka Actions → Update profile metrics → Run workflow. Workflow memakai GITHUB_TOKEN repository untuk menulis SVG; METRICS_TOKEN untuk membaca statistik.
5. Setelah github-metrics.svg muncul di root repository, hapus pembungkus komentar HTML pada bagian GitHub activity di README.

Jadwal pembaruan: sekitar pukul 06.00 WIB setiap hari; GitHub dapat menunda scheduled runs. Jika pembaruan gagal, SVG terakhir tetap tersimpan. Scheduled workflows pada repository publik yang tidak aktif dapat dinonaktifkan GitHub.

Workflow belum dijalankan di akunmu. uses: lowlighter/metrics@latest mengikuti contoh upstream; untuk versi yang terkunci, ganti latest dengan full commit SHA yang kamu tinjau.

## Pilihan widget

- Skill Icons: https://github.com/tandpfun/skill-icons — dipakai di README. Teks teknologi tetap terbaca apabila layanan ikon gagal.
- Metrics: https://github.com/lowlighter/metrics — pilihan statistik dan bahasa; workflow opsional disertakan.
- GitHub Stats: https://github.com/jstrieb/github-stats — alternatif grafik statistik berbasis GitHub Actions; tidak perlu dipasang bersamaan dengan Metrics.

Banner GIF pihak ketiga, animasi sapaan, dan endpoint kartu statistik publik dari README lama dihapus untuk mengurangi ketergantungan eksternal. Tautan proyek menggunakan repository langsung. Tidak ada situs demo atau URL OpenNexus yang ditebak.

Pemeriksaan sumber dilakukan 17 November 2026. Repository proyek dan dokumentasi widget ditemukan melalui web. Pemeriksaan ini bukan jaminan uptime endpoint atau keberadaan akun sosial di masa depan.
