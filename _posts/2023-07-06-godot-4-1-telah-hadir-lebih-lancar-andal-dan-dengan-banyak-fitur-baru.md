---
layout: post
title: 'Godot 4.1 Telah Hadir, Lebih Lancar, Andal, dan Dengan Banyak Fitur Baru'
date: 2023-07-06 18:29 +0700
categories: [Berita]
---
Setelah [empat bulan pengembangan](https://godotengine.org/article/godot-4-0-sets-sail), kami dengan bangga mempersembahkan Godot 4.1! Ini adalah pembaruan yang mengikuti janji kami untuk terus meningkatkan Godot 4.0 dengan rilis inkremental yang sering, dengan fokus pada stabilitas, performa, dan penampilan yang lebih baik.

Seperti biasa, rilis baru ini dilengkapi dengan sejumlah fitur baru yang menyenangkan, seperti peningkatan pada penghindaran navigasi AI dan kemampuan untuk memisahkan editor kode dan menampilkannya di layar lain.

![Editor kode dipisahkan dari jendela editor utama](https://godotengine.org/storage/blog/godot-4-1-is-here/detached-code-editor.png)

Namun, kami juga sangat memperhatikan prioritas perbaikan bug yang ditemui dalam Godot 4.0. Pembaruan ini memperbaiki lebih dari 900 masalah yang dilaporkan oleh pengguna saat menggunakan Godot 4 atau saat membantu kontributor menguji 4.1 dengan versi pra-rilis. Secara keseluruhan, mesin ini seharusnya terasa lebih andal. Kami akan terus meningkatkan stabilitas, performa, dan alur kerja dengan setiap rilis fitur Godot 4 yang akan datang.

Bagi sebagian besar game dan aplikasi yang dibuat dengan Godot 4.0, beralih ke versi 4.1 seharusnya relatif aman. Kami sedang [menyiapkan panduan migrasi](https://github.com/godotengine/godot-docs/pull/7611) yang menjelaskan semua hal yang perlu diperhatikan saat bermigrasi proyek Anda. Beberapa ketidakcocokan diharapkan terjadi khususnya untuk pengguna C# dan GDExtension, namun kami berusaha untuk menghindarinya pada rilis-rilis berikutnya. Jangan lupa selalu membuat cadangan saat beralih versi, bahkan untuk versi minor. Lebih baik lagi, disarankan untuk menggunakan sistem kontrol versi seperti Git dan melakukan commit pada versi proyek Anda sebelum bermigrasi.

**Jika Anda ingin segera mencobanya, Anda dapat [mengunduh Godot 4.1 sekarang](https://godotengine.org/download/).** Atau tetap disini dan baca lebih lanjut tentang perubahan paling menonjol dalam rilis ini. Anda juga dapat menonton video sorotan yang bagus ini dari [GDQuest](https://www.gdquest.com/):

<iframe width="560" height="315" src="https://www.youtube.com/embed/PAtG_fHhIx8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Memberikan Dukungan

Sebagai upaya komunitas, Godot bergantung pada kontributor individu untuk melakukan perbaikan. Dalam beberapa tahun terakhir, [donasi pengguna dan perusahaan](https://godotengine.org/donate/)

telah memungkinkan kami untuk juga mempekerjakan sejumlah kontributor inti untuk bekerja penuh waktu pada mesin ini dan membawa Anda rilis yang cepat.

Pengeluaran bulanan kami masih lebih tinggi daripada sumbangan bulanan, dan kami masih bergantung pada sumbangan besar dari perusahaan untuk mendanai pengembangan. Saat ini, kami membutuhkan lebih banyak [sumbangan bulanan](https://godotengine.org/donate/) untuk terus mempertahankan kecepatan pembaruan Godot 4, belum lagi kebutuhan untuk mempekerjakan lebih banyak pengelola untuk meninjau setiap kontribusi.

Selain dukungan keuangan, Anda juga dapat memberikan dukungan dengan: menulis laporan bug yang detail, berkontribusi pada kode sumber, menulis dokumentasi, menulis panduan (untuk dokumen resmi atau di situs web Anda sendiri), dan memberikan dukungan kepada orang lain di berbagai [platform komunitas](https://docs.godotengine.org/en/latest/community/channels.html) dengan menjawab pertanyaan dan memberikan tips yang berguna.

Terakhir, tetapi tidak kalah pentingnya, membuat game dengan Godot dan memberikan kredit kepada mesin tersebut dapat membantu mempopulerkan Godot dan meyakinkan lebih banyak orang untuk berkontribusi dan meningkatkan Godot untuk semua orang. Ingat, kita semua saling mendukung dan Godot membutuhkan dukungan komunitas di setiap bidang untuk berkembang.

## Sorotan

Rilis ini dapat terwujud berkat kontribusi dari lebih dari 300 kontributor! Kami mengucapkan terima kasih atas kerja keras dan dedikasi Anda semua, termasuk mereka yang membantu kami menguji mesin sebelum rilis dan melaporkan bug.

Untuk daftar lengkap semua perbaikan bug dan perbaikan yang ada, kunjungi [changelog interaktif](https://godotengine.github.io/godot-interactive-changelog/#4.1) kami.

Tanpa basa-basi lagi, berikut adalah rincian perubahan utama dan fitur baru.

### Performa

Game Godot dibangun sebagai pohon node, yang merupakan blok dasar mesin untuk entitas game. Menambahkan dan menghapus node adalah operasi yang harus dilakukan mesin dengan sangat sering, sehingga harus dilakukan dengan secepat mungkin.

Pada Godot 4.1, kami mengubah algoritma untuk menggunakan hashmap yang cepat sehingga menambah dan menghapus child node menjadi beberapa kali lebih cepat. Operasi node yang jarang digunakan sedikit lebih lambat sebagai akibatnya, dan penggunaan memori pada kelas Node dasar meningkat sebesar 10%, namun ini adalah trade-off yang kecil dan diperlukan untuk mendapatkan manfaat besar bagi semua pengguna Godot, terutama untuk proyek-proyek yang kompleks dengan banyak manipulasi node.

Versi ini juga memperkenalkan multithreading eksperimental untuk scene Anda, fitur yang dimulai oleh [Juan Linietsky](https://github.com/reduz). Properti node baru memberi Anda kontrol penuh atas bagaimana node-node tersebut diproses, secara berurutan atau secara paralel.

![Opsi konfigurasi

thread group untuk Node](https://godotengine.org/storage/blog/godot-4-1-is-here/threaded-node-properties-highlighted.png)

Seperti yang disebutkan sebelumnya, fitur ini saat ini ditandai sebagai eksperimental karena membutuhkan pengujian yang ekstensif untuk menemukan kasus-kasus yang spesifik. Kami tidak merekomendasikan menggunakannya secara langsung pada produksi. Namun, fitur ini memberikan dasar untuk memaksimalkan penggunaan perangkat keras modern dengan kontrol yang sederhana.

Juga dalam hal multithreading, [Pedro J. Estébanez](https://github.com/RandomShaper) telah bekerja keras untuk memperbaiki banyak masalah dan batasan dalam proses multi-threaded loading.

Pada sisi rendering, renderer Vulkan telah mendapatkan pipeline cache. Meskipun Godot sudah memiliki cache shader untuk mengurangi hambatan saat kompilasi shader, kompilasi pipeline masih menyebabkan sedikit hambatan dan waktu muat yang lebih lambat. Meskipun masalah stuttering pada kompilasi pipeline masih jauh dari terselesaikan, ini merupakan langkah yang tepat dan seharusnya mengurangi sedikit waktu muat saat menggunakan salah satu backend rendering berbasis RenderingDevice. Cache ini dapat dinonaktifkan dalam pengaturan proyek dan diaktifkan secara default di Godot 4.1.

![Pengaturan cache shader pada pengaturan proyek](https://godotengine.org/storage/blog/godot-4-1-is-here/shader-cache-setting.png)

Peningkatan ini belum menangani semua penyebab kemacetan yang mungkin terjadi, namun ini adalah langkah pertama yang tepat dan akan terus kami tingkatkan pada rilis mendatang.

Lebih banyak pekerjaan akan dilakukan dalam bidang performa sepanjang tahun ini.

### Inti

Ketika mengimpor model ke Godot, sering kali ada masalah bahwa model tersebut menghadap ke belakang.

![Sebuah model yang menghadap ke belakang (sebelum perubahan)](https://godotengine.org/storage/blog/godot-4-1-is-here/model-facing-back.webp)

[Juan Linietsky](https://github.com/reduz), [Tokage](https://github.com/TokageItLab), dan [Aaron Franke](https://github.com/aaronfranke) mengatasi masalah ini dengan menukar arah depan dan belakang kamera di editor. Selain itu, fungsi `look_at()` kini memiliki argumen untuk menggunakan model space sebagai referensi untuk menghadap ke depan bukan sumbu minus Z kamera. Perubahan ini juga membantu memperbaiki bug lama dalam path following.

![Sebuah model yang menghadap ke depan (setelah perubahan)](https://godotengine.org/storage/blog/godot-4-1-is-here/model-facing-front.webp)

Pembaruan ini juga membawa penghalusan delta frame ke Godot 4, oleh [lawnjelly](https://github.com/lawnjelly). Hal ini dapat secara signifikan meningkatkan kelancaran pergerakan dan memberikan gameplay yang lebih halus. Opsi ini diaktifkan secara default, namun perlu diingat bahwa ini hanya berfungsi ketika VSync juga diaktifkan.

### Scripting

#### GDScript

Hingga saat ini, dalam GDScript, Anda harus menggunakan resource atau autoload untuk ber

bagi data antara beberapa instance dari script yang sama.

Berkat [George Marques](https://github.com/vnen), sekarang Anda dapat membuat dan menggunakan variabel statis. Variabel statis menyimpan data pada kelas bukan pada setiap instance, sehingga data tersebut dibagikan di antara setiap instance dari kelas tersebut.

Untuk membuat variabel statis, tambahkan kata kunci `static` di depan variabel yang didefinisikan di bagian atas script Anda.

![Contoh kode GDScript yang menunjukkan penggunaan variabel statis](https://godotengine.org/storage/blog/godot-4-1-is-here/gdscript-static-variables.png)

Fitur hebat lain dari GDScript yang ditambahkan dalam Godot 4 adalah generasi otomatis halaman dokumentasi untuk kelas-kelas bernama Anda.

![Contoh dokumentasi yang dihasilkan berdasarkan kelas GDScript kustom](https://godotengine.org/storage/blog/godot-4-1-is-here/gdscript-docs-generation.png)

Versi ini juga mencakup pembaruan sistem oleh [ocean](https://github.com/anvilfolk) yang sekarang memperlakukan enumerasi sebagai tipe data, sehingga dokumentasi yang dihasilkan lebih tepat. Anda juga sekarang dapat menggunakan docstring dalam baris kode daripada selalu harus menempatkannya di atas definisi variabel atau fungsi.

```gdscript
var my_variable = 10 ## Ini adalah docstring dalam baris kode
```

#### C#/.NET

Fokus pada rilis ini adalah untuk menyamakan fitur antara C# dan GDScript.

Ketika menggunakan GDScript, Anda dapat dengan mudah menggunakan variabel statis untuk berbagi data antara instance dari script yang sama. Dalam C#, fitur ini belum tersedia secara langsung. Namun, dalam Godot 4.1, [George Marques](https://github.com/vnen) telah menambahkan dukungan untuk variabel statis dalam C#.

Untuk membuat variabel statis dalam C#, Anda dapat menggunakan kata kunci `static` sebelum deklarasi variabel, seperti contoh berikut:

```csharp
static int myVariable = 10;
```

Dengan menggunakan variabel statis, data yang disimpan dalam variabel tersebut akan bersifat global dan dapat diakses oleh semua instance dari script yang sama. Ini memudahkan pertukaran data antara instance-instance tersebut tanpa perlu menggunakan resource atau autoload.

Selain itu, dalam Godot 4.1, ada perbaikan signifikan dalam editor kode C#. Fitur-fitur seperti penyelesaian otomatis dan navigasi kode telah ditingkatkan, sehingga membuat pengembangan dengan C# menjadi lebih mudah dan efisien.

### Peningkatan Editor

Editor Godot juga mengalami sejumlah peningkatan dalam Godot 4.1. Salah satunya adalah kemampuan untuk memisahkan editor kode dan menampilkannya di layar lain. Fitur ini sangat berguna bagi pengembang yang memiliki beberapa monitor, karena mereka dapat memanfaatkan ruang kerja yang lebih luas untuk melihat dan mengedit kode mereka secara lebih efisien.

Selain itu, pengeditan tampilan skrip juga telah ditingkatkan. Sekarang, ketika Anda mengedit skrip, tampilan editor kode akan menyoroti baris-baris yang mengandung kode yang sedang diedit, sehingga memudahkan Anda dalam melacak perubahan yang Anda buat.

### Peningkatan AI Navigation dan Pathfinding

Dalam Godot 4.1, terdapat sejumlah peningkatan pada penghindaran navigasi AI dan pathfinding. Sekarang, mesin Godot memiliki algoritma yang lebih baik untuk menghindari tabrakan antara agen navigasi AI yang bergerak di sekitar lingkungan. Hal ini memungkinkan agen navigasi untuk bergerak dengan lebih lancar dan menghindari rintangan dengan lebih baik.

Selain itu, terdapat peningkatan pada performa pathfinding, yang memungkinkan pencarian jalur yang lebih cepat dan lebih efisien. Ini sangat berguna dalam game yang memiliki banyak entitas yang bergerak secara independen dan memerlukan perhitungan jalur yang kompleks.

### Peningkatan Performa Rendering

Godot 4.1 juga menyertakan beberapa peningkatan performa dalam hal rendering. Renderer Vulkan telah ditingkatkan dengan penambahan cache pipeline, yang mengurangi stuttering saat kompilasi shader. Meskipun masalah stuttering kompilasi pipeline belum sepenuhnya teratasi, ini merupakan langkah positif menuju peningkatan performa secara keseluruhan.

Selain itu, Godot 4.1 juga memperkenalkan teknik pengurangan jittering pada rendering, yang menghasilkan pergerakan yang lebih halus dan visual yang lebih rapi

dalam game. Hal ini dilakukan dengan menggunakan metode smoothing pada delta frame, sehingga mengurangi lonjakan perubahan posisi antara frame yang berbeda.

### Perbaikan Bug dan Peningkatan Lainnya

Selain peningkatan yang disebutkan di atas, Godot 4.1 juga mencakup perbaikan bug dan peningkatan lainnya yang signifikan. Lebih dari 900 masalah yang dilaporkan oleh pengguna telah diperbaiki dalam rilis ini, termasuk masalah stabilitas, kinerja, dan workflow. Hal ini membuat mesin Godot lebih dapat diandalkan dan nyaman digunakan oleh para pengembang.

Beberapa perbaikan bug dan peningkatan lainnya yang diimplementasikan dalam Godot 4.1 meliputi:

- Perbaikan dalam mekanisme impor model 3D untuk mengatasi masalah orientasi model yang salah.
- Peningkatan editor kode C# dengan fitur penyelesaian otomatis dan navigasi yang lebih baik.
- Peningkatan editor dengan kemampuan untuk memisahkan editor kode dan menampilkannya di layar lain.
- Peningkatan dalam penghindaran navigasi AI untuk menghindari tabrakan antara agen navigasi.
- Peningkatan performa pathfinding untuk pencarian jalur yang lebih cepat dan lebih efisien.
- Peningkatan performa rendering dengan pengurangan stuttering saat kompilasi shader dan pengurangan jittering pada pergerakan visual.

### Ringkasan

Godot 4.1 adalah rilis yang sangat dinantikan dengan sejumlah perbaikan bug, peningkatan performa, dan fitur baru. Rilis ini menunjukkan komitmen pengembang Godot dalam meningkatkan pengalaman pengguna dan memberikan alat yang lebih baik bagi para pengembang game.

Dengan peningkatan dalam performa, stabilitas, dan workflow, Godot 4.1 memberikan lingkungan pengembangan yang lebih baik dan memungkinkan para pengembang untuk membuat game yang lebih menarik dan berkualitas.

Jika Anda tertarik untuk mencoba Godot 4.1, Anda dapat mengunduhnya sekarang dan mulai menjelajahi semua fitur baru dan peningkatan yang ditawarkan. Selamat mengembangkan game dengan Godot 4.1!

Pranala Sumber: [https://godotengine.org/article/godot-4-1-is-here/](https://godotengine.org/article/godot-4-1-is-here/)

[def]: https://godotengine.org/