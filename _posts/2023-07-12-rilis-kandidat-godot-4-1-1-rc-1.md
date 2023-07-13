---
layout: post
title: 'Rilis Kandidat: Godot 4.1.1 RC 1'
excerpt: "Putaran pertama perbaikan bug dan peningkatan penggunaan untuk Godot 4.1 siap untuk dipertimbangkan!"
date: 2023-07-12 19:30 +0700
image: https://godotengine.org/storage/blog/covers/release-candidate-godot-4-1-1-rc-1.webp
image_caption_title: "Entri GMTK Game Jam"
image_caption_description: ""
categories: [Berita]
---

Ini adalah akhir pekan sibuk di Godot-land, karena [Godot 4.1 yang baru dirilis](/posts/godot-4-1-telah-hadir-lebih-lancar-andal-dan-dengan-banyak-fitur-baru/) sedang dilihat, diuji, dan dicoba oleh ribuan pengembang. GMTK Game Jam tahunan oleh saluran YouTube populer [Game Maker's Toolkit]() sangat membantu dalam hal itu! Tentu saja, di mana ada banyak pengguna, ada juga banyak laporan dan saran yang sangat dihargai. Selain itu, kami juga memiliki beberapa laporan yang siap digunakan sebelum 4.1 dijamin dan dikirim.

Seperti biasa dengan rilis perawatan pertama (juga dikenal sebagai "rilis patch"), fokusnya adalah segera menangani masalah dan isu yang mendesak, kemungkinan adanya regresi dan kegagalan, serta beberapa aliasing dalam berbagai alur kerja. Beberapa perubahan paling penting meliputi:

- Perbaikan untuk kegagalan akibat perulangan tak terbatas di `AnimationStateMachine` ([GH-79141](https://github.com/godotengine/godot/pull/79141)). Ini adalah masalah yang rumit karena mudah dipicu dengan konfigurasi minimum. Sekarang, ketergantungan sirkular dideteksi dengan benar untuk mencegah perulangan tak terbatas.

- Ekspor baris perintah proyek C#/.NET tidak lagi menghilangkan file secara acak ([GH-79173](https://github.com/godotengine/godot/pull/79173)). Ekspor Anda mungkin kehilangan beberapa sumber daya sembarang (bukan skrip C#, tetapi gambar, misalnya), jika Anda meng-ekspor proyek Anda dengan CLI. Ini tidak akan terjadi lagi.

- Opsi ekspor kustom yang dapat Anda tentukan dengan `EditorExportPlugin` sekarang dipulihkan dengan benar saat editor dijalankan ulang ([GH-79025](https://github.com/godotengine/godot/pull/79025)). Sebelumnya, kegunaan fitur yang baru ditambahkan ini terbatas karena adanya kehilangan data antara sesi.

- Untuk pengguna Linux, ada perbaikan potensial untuk pembekuan saat berinteraksi dengan menu di Wayland ([GH-79143](https://github.com/godotengine/godot/pull/79143)). Ini adalah masalah yang sulit diidentifikasi dan di-debug, tetapi penggemar Wayland lokal kami berhasil menemukan penyebab yang mungkin dan memvalidasi bahwa perilaku yang tidak diinginkan telah diatasi.

[Lompat ke bagian **Unduhan**](#unduhan), dan cobalah sekarang, atau lanjutkan membaca untuk mempelajari lebih lanjut tentang peningkatan dalam rilis ini. Anda juga dapat [mencoba **editor web**](https://editor.godotengine.org/releases/4.1.1.rc1/) atau **editor Android** untuk rilis ini. Jika Anda tertarik dengan yang terakhir, harap minta bergabung [dengan grup pengujian kami](https://groups.google.com/g/godot-testers) untuk mendapatkan akses ke versi pra-rilis.

-----

*Gambar ilustrasi untuk artikel ini menampilkan enam entri menakjubkan dari [GMTK Game Jam](https://itch.io/jam/gmtk-2023) terbaru — semuanya dibuat dengan Godot! Cobalah, tinggalkan komentar untuk pengembang, dan, tentu saja, pertimbangkan memberikan suara ❤️ Banyak pengembang game lain memilih Godot untuk game jam ini, jadi pastikan untuk memeriksa daftar lengkap entri dan dukung para pembuat karya Anda. Game yang diilustrasikan dalam gambar sampul adalah sebagai berikut:*

- [**Yeti Upsetti**](https://miltage.itch.io/yeti-upsetti) *— reimajinasi SkiFree klasik; dibuat dengan Godot 4.1.*
- [**Making the Game**](https://kindanice.itch.io/making-the-game) *memungkinkan Anda membuat keputusan desain game dan menderita konsekuensinya; didukung oleh Godot 3.5.1.*
- [**Tama-Get-Out!**](https://jrileyh.itch.io/tama-get-out) *memungkinkan Anda mengisi sepatu hewan peliharaan saku; dikembangkan dengan Godot 4.1.*
- [**Levelrinth**](https://dunkelgrau.itch.io/gmtk23) *— platformer teka-teki di mana Anda adalah levelnya; dibuat dengan Godot 4.1.*
- [**poki**](https://slimewitch.itch.io/poki) *— permainan teka-teki kreatif yang memungkinkan Anda membangun kembali level sebelum memecahkannya; dibuat dengan Godot 4.1.*
- [**Video Editor's Toolkit**](https://patrickgh3.itch.io/video-editors-toolkit) *memungkinkan Anda bertanggung jawab untuk membuat video yang mencakup GMTK Game Jam 2023; dikembangkan dengan Godot 3.5.2.*

## Apa yang baru

46 kontributor mengirimkan lebih dari 70 perbaikan untuk rilis ini. Anda dapat meninjau daftar lengkap perubahan dengan [changelog interaktif kami](https://godotengine.github.io/godot-interactive-changelog/#4.1.1-rc1), yang berisi tautan ke commit dan PR yang relevan untuk rilis ini dan rilis sebelumnya. Berikut adalah perubahan paling signifikan:

- 2D: Memperbaiki penarikan string di editor tiledata ([GH-78522](https://github.com/godotengine/godot/pull/78522)).
- 2D: Pastikan tombol pintas mengikuti konteks di `TileSetAtlasSourceEditor` ([

GH-78920](https://github.com/godotengine/godot/pull/78920)).
- 3D: Memperbaiki metode `project_*` pada Camera3D yang tidak memperhitungkan frustum offset ([GH-75806](https://github.com/godotengine/godot/pull/75806)).
- 3D: Memperbaiki tampilan grid viewport 3D yang hilang saat tab scene berubah ([GH-78694](https://github.com/godotengine/godot/pull/78694)).
- Animasi: Memperbaiki cek status perulangan tak terbatas di `AnimationStateMachine` ([GH-79141](https://github.com/godotengine/godot/pull/79141)).
- Animasi: Tambahkan kompatibilitas 3.x untuk mode loop animasi ([GH-79155](https://github.com/godotengine/godot/pull/79155)).
- Buildsystem: Linux: Memungkinkan pemisahan paket brotli untuk menggunakan pustaka sistem ([GH-79101](https://github.com/godotengine/godot/pull/79101)).
- C#: Perbarui RiderPathLocator untuk mendukung JetBrains Toolbox 2.0 ([GH-78832](https://github.com/godotengine/godot/pull/78832)).
- C#: Bandingkan nama simbol tanpa status aliran null ([GH-79094](https://github.com/godotengine/godot/pull/79094)).
- C#: Perbaiki ekspor baris perintah ([GH-79173](https://github.com/godotengine/godot/pull/79173)).
- Inti: Periksa kevalidan parameter di `Object::set_script` ([GH-46125](https://github.com/godotengine/godot/pull/46125)).
- Inti: Perbaiki WorkerThreadPool berukuran nol yang tidak memproses tugas kelompok ([GH-78845](https://github.com/godotengine/godot/pull/78845)).
- Inti: Perbaiki pemeriksaan induk di `Node::add_sibling` ([GH-78847](https://github.com/godotengine/godot/pull/78847)).
- Inti: Perbaiki kesalahan saat karakter non-ASCII dalam path resource pack ([GH-78935](https://github.com/godotengine/godot/pull/78935)).
- Inti: Perbaiki `PackedScene::get_last_modified_time()` selalu mengembalikan `0` ([GH-79237](https://github.com/godotengine/godot/pull/79237)).
- Editor: Fokus pada node saat menghubungkan ([GH-54071](https://github.com/godotengine/godot/pull/54071)).
- Editor: Konverter proyek: Gunakan driver render yang sama dengan Manajer Proyek ([GH-78795](https://github.com/godotengine/godot/pull/78795)).
- Editor: Perbaiki penyeretan file dari `res://` ke `res://` ([GH-78914](https://github.com/godotengine/godot/pull/78914)).
- Editor: Jangan mengubah nama unik node menjadi nama yang sama ([GH-78925](https://github.com/godotengine/godot/pull/78925)).
- Ekspor: Perbaiki opsi ekspor dari `EditorExportPlugin` yang di-script ([GH-79025](https://github.com/godotengine/godot/pull/79025)).
- GDScript: Perbaiki regresi dengan deskripsi enum GDScript yang sekarang muncul dalam dokumentasi ([GH-78953](https://github.com/godotengine/godot/pull/78953)).
- GUI: Perbaiki perilaku kursor untuk multiseleksi di Pohon saat menahan CTRL ([GH-71024](https://github.com/godotengine/godot/pull/71024)).
- GUI: Pastikan bahwa `_drop_physics_mouseover` hanya terjadi ketika diperlukan ([GH-78078](https://github.com/godotengine/godot/pull/78078)).
- GUI: Perbaiki ukuran minimum yang tidak valid untuk pesan terjemahan di tombol opsi ([GH-78835](https://github.com/godotengine/godot/pull/78835)).
- Impor: Perbaiki batasan tipe string dan mode penggantian nama kelas hint properti ([GH-79139](https://github.com/godotengine/godot/pull/79139)).
- Navigasi: Perbaiki posisi jalur navigasi terdekat yang mungkin ([GH-79004](https://github.com/godotengine/godot/pull/79004)).
- Jaringan: Perbaiki panggilan `rpc` dengan bind ([GH-78551](https://github.com/godotengine/godot/pull/78551)).
- Partikel: Inisialisasi buffer instance partikel jika digunakan sebelum diperbarui ([GH-78852](https://github.com/godotengine/godot/pull/78852)).
- Partikel: Satukan kondisi kesalahan untuk waktu hidup jejak partikel ([GH-79270](https://github.com/godotengine/godot/pull/79270)).
- Porting: Perbaiki format pesan kesalahan `dlopen` ([GH-78802](https://github.com/godotengine/godot/pull/78802)).
- Porting: Perbaiki logika cadangan dari `OS::shell_show_in_file_manager` ([GH-79087](https://github.com/godotengine/godot/pull/79087)).
- Porting: Linux/BSD: Hindari pembekuan saat berinteraksi dengan menu di Wayland ([GH-79143](https://github.com/godotengine/godot/pull/79143)).
- Porting: Linux/BSD: Perbaiki `move_to_trash` yang salah melaporkan file tidak ditemukan ([GH-79284](https://github.com/godotengine/godot/pull/79284)).
- Porting: Windows: Sorot baik judul jendela maupun tombol taskbar saat `request_attention` ([GH-78263](https://github.com/godotengine/godot/pull/78263)).
- Porting: Windows: Perbaiki pengaturan mode jendela awal yang bukan eksklusif ([GH-79016](https://github.com/godotengine/godot/pull/79016)).
- Rendering: Bersihkan buffer specular jika mode langit adalah kanvas dan efek ruang layar digunakan ([GH-78624](https://github.com/godotengine/godot/pull/78624)).
- Rendering: Perbaiki bug

 threading pada perangkat rendering Vulkan ([GH-78794](https://github.com/godotengine/godot/pull/78794)).
- Rendering: Ambil offset mata ke dalam akun untuk kedalaman pada StandardMaterial3D ([GH-79049](https://github.com/godotengine/godot/pull/79049)).
- Shader: Perbaiki kompilasi shader yang tidak valid saat menggunakan `hint_normal_roughness_texture` di backend mobile ([GH-78839](https://github.com/godotengine/godot/pull/78839)).
- Shader: Perbaiki penggunaan akhiran uint pada deklarasi angka heksadesimal di shader ([GH-78906](https://github.com/godotengine/godot/pull/78906)).
- Shader: Perbaiki presisi pemotongan literal float dalam bahasa shader ([GH-78972](https://github.com/godotengine/godot/pull/78972)).
- Shader: Perbaiki komentar dan indentasi dalam file `.gdshaderinc` ([GH-79158](https://github.com/godotengine/godot/pull/79158)).

Satu perubahan yang sebelumnya diterima dihapus dalam rilis ini karena regresi.

- GUI: Batalkan "Perbaiki kehilangan fokus `AcceptDialog` non-eksklusif dengan `close_on_escape`" ([GH-79084](https://github.com/godotengine/godot/pull/79084)).

Rilis ini dibangun dari commit [`e709ad4d6`](https://github.com/godotengine/godot/commit/e709ad4d6407e52dc62f00a471d13eb6c89f2c4c) (lihat [README](https://downloads.tuxfamily.org/godotengine/4.1.1/rc1/README.txt)).

## Unduhan

Unduhan untuk versi pra-rilis ini dapat ditemukan di repositori GitHub kami:

* [**Unduh Godot 4.1.1 RC 1**](https://github.com/godotengine/godot-builds/releases/tag/4.1.1-rc1).

**Build standar** mencakup dukungan untuk GDScript dan GDExtension.

**Build .NET 6** (ditandai sebagai `mono`) mencakup dukungan untuk C#, serta GDScript dan GDExtension.
- Build .NET memerlukan [.NET SDK 6.0](https://dotnet.microsoft.com/en-us/download/dotnet/6.0) atau [7.0](https://dotnet.microsoft.com/en-us/download/dotnet/7.0) terpasang di lokasi standar.

## Masalah yang Diketahui

Saat ini tidak ada masalah yang diketahui yang diperkenalkan oleh rilis ini.

Dengan setiap rilis, kami menerima bahwa akan ada berbagai masalah yang sudah dilaporkan tetapi belum diperbaiki. Lihat pelacak masalah GitHub untuk daftar lengkap [masalah yang diketahui](https://github.com/godotengine/godot/issues?q=is%3Aissue+is%3Aopen+label%3Abug+).

## Laporan Bug

Sebagai pengujian, kami mendorong Anda untuk [membuka laporan bug](https://github.com/godotengine/godot/issues) jika Anda mengalami masalah dengan rilis ini. Harap periksa [masalah yang ada di GitHub](https://github.com/godotengine/godot/issues) terlebih dahulu, menggunakan fungsi pencarian dengan kata kunci yang relevan, untuk memastikan bahwa bug yang Anda alami belum diketahui.

Terutama, setiap perubahan yang akan menyebabkan regresi dalam proyek Anda sangat penting untuk dilaporkan (misalnya jika sesuatu yang berfungsi dengan baik dalam rilis 4.1, tetapi tidak lagi berfungsi dalam 4.1.1 RC 1).

## Dukungan

Godot adalah mesin permainan sumber terbuka dan nirlaba yang dikembangkan oleh ratusan kontributor pada waktu luang mereka, dan beberapa pengembang paruh atau penuh waktu yang disewa berkat [donasi dari komunitas Godot](https://godotengine.org/donate). Terima kasih banyak kepada semua orang yang telah [berkontribusi waktu](https://github.com/godotengine/godot/blob/master/AUTHORS.md) atau [dukungan keuangan](https://github.com/godotengine/godot/blob/master/DONORS.md) ke proyek ini!

Jika Anda ingin mendukung proyek secara finansial dan membantu kami mengamankan perekrutan masa depan, Anda dapat melakukannya di [Patreon](https://www.patreon.com/godotengine) atau [PayPal](https://godotengine.org/donate).

[Pranala Sumber](https://godotengine.org/article/release-candidate-godot-4-1-1-rc-1/)