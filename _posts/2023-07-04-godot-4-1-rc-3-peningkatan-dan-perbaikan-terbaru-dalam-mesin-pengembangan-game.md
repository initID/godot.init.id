---
layout: post
title: 'Godot 4.1 RC 3: Peningkatan dan Perbaikan Terbaru dalam Mesin Pengembangan
  Game'
date: 2023-07-04 23:28 +0700
categories: [Berita]
---

Godot 4.1 RC 3 adalah rilis kandidat terbaru dari Godot, mesin pengembangan game open source. Rilis ini menawarkan sejumlah perbaikan dan pembaruan yang telah dilakukan untuk meningkatkan pengalaman pengguna. Regresi atau bug yang baru ditemukan dalam versi 4.0 juga telah diperbaiki dalam rilis ini.

Selama fase pengujian beta dan dengan dua rilis kandidat sebelumnya, kami berhasil mengidentifikasi dan memperbaiki sejumlah regresi yang dapat mempengaruhi pengalaman pengguna dibandingkan dengan Godot 4.0. Kami cukup yakin bahwa sebagian besar masalah tersebut telah ditangani, dan masalah yang tersisa akan diperbaiki dalam rilis pemeliharaan 4.1.x di masa depan.

Para kontributor kami berhasil memperbaiki beberapa regresi kritis selama fase pengujian RC 2, yang membenarkan pembuatan rilis kandidat ketiga untuk memvalidasi perubahan-perubahan tersebut. Jika semuanya berjalan lancar, kami berada dalam jalur yang tepat untuk merilis versi 4.1 dalam beberapa hari mendatang. Harap terus melaporkan masalah yang Anda temui dengan RC ini, meskipun Anda tidak menganggapnya kritis – kami dapat memberikan prioritas pada masalah-masalah tersebut di awal siklus pengembangan 4.2, dan memasukkan perbaikan-perbaikan tersebut ke dalam rilis 4.1.x.

Rilis ini menyertakan sejumlah perbaikan dibandingkan dengan Godot 4.0 yang telah diterbitkan sebelumnya tahun ini. Beberapa sistem juga telah dikerjakan ulang, yang berarti proyek-proyek yang bergantung pada sistem-sistem tersebut perlu diperbarui. Namun, bagi sebagian besar game dan aplikasi yang dibuat dengan Godot 4.0, seharusnya aman untuk bermigrasi ke versi 4.1. Jangan lupa selalu membuat cadangan saat beralih versi, bahkan untuk versi minor. Lebih baik lagi, gunakan sistem kontrol versi seperti Git dan lakukan commit pada versi proyek Anda sebelum migrasi.

**"What's new"** - Ada beberapa perubahan utama dalam Godot 4.1, dan Anda dapat membaca lebih lanjut tentangnya dalam pengumuman sebelumnya. Di bawah ini adalah perubahan-perubahan yang paling signifikan dibandingkan dengan 4.1 RC 2:

- C#: Memperbaiki kesalahan penyelesaian NodePaths yang tidak dipanggil dari thread utama (GH-78928).
- Core: Memperbaiki pengelolaan flag safe-for-nodes pada ResourceLoader dan WorkerThreadPool (GH-78974).
- Core: Perbaikan sementara crash saat memuat sumber daya akibat TLS yang bermasalah (GH-78977).
- Editor: Memperbaiki seleksi node yang tidak ditangani dengan benar

 saat diluncurkan (GH-78980).
- GDExtension: Memperbaiki GDVIRTUAL_NATIVE_PTR dengan menambahkan specializations yang hilang pada VariantInternalAccessor (GH-78971).
- GUI: Memperbaiki pembaruan keterlihatan scrollbar pada RichTextLabel dengan multi-threading (GH-78968).
- GUI: Mencegah crash saat memproses cache baris pada RichTextLabel (GH-78975).
- Navigation: Memperbaiki kecepatan penghindaran berlanjut pada NavigationAgent (GH-78850).
- Navigation: Memperbaiki pembaruan posisi pada NavigationAgent yang tidak selalu terjadi (GH-78857).
- Navigation: Memperbaiki crash pada NavigationAgent3D (GH-78939).

**"Downloads"** - Anda dapat mengunduh rilis ini langsung dari repositori kami. Terdapat dua opsi unduhan yang tersedia:

- Standard build (GDScript, GDExtension).
- .NET 6 build (C#, GDScript, GDExtension). Membutuhkan .NET SDK 6.0 atau 7.0 yang terpasang di lokasi standar.

**"Known issues"** - Seperti setiap rilis, ada kemungkinan adanya beberapa masalah yang telah dilaporkan namun belum diperbaiki. Anda dapat melihat daftar bug yang diketahui dalam versi 4.1 pada GitHub issue tracker.

**"Bug reports"** - Kami mendorong Anda sebagai pengujian untuk membuka laporan bug jika Anda mengalami masalah dengan rilis ini. Silakan periksa isu-isu yang sudah ada di GitHub terlebih dahulu dengan menggunakan fungsi pencarian dengan kata kunci relevan untuk memastikan bahwa bug yang Anda alami belum diketahui. Terutama, laporan mengenai perubahan yang menyebabkan regresi pada proyek Anda sangat penting untuk dilaporkan.

**"Support"** - Godot adalah mesin pengembangan game open source yang dikembangkan oleh ratusan kontributor pada waktu luang mereka, dengan dukungan keuangan dari komunitas Godot. Kami mengucapkan terima kasih kepada semua orang yang telah menyumbangkan waktu atau dukungan finansial mereka untuk proyek ini. Jika Anda ingin mendukung proyek ini secara finansial dan membantu kami dalam merekrut pengembang di masa depan, Anda dapat melakukannya melalui Patreon atau PayPal.

[Pranala Sumber](https://godotengine.org/article/release-candidate-godot-4-1-rc-3/)