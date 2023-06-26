---
layout: post
title: Sekilas Contoh GDScript - Pengantar untuk Pemula
date: 2023-06-26 08:08 +0700
categories: [Uncategorized]
tags: []
mermaid: true
---

GDScript merupakan bahasa pemrograman yang powerful dan mudah dipahami yang digunakan dalam Godot Game Engine. Dengan GDScript, Anda dapat mengembangkan game interaktif dan menarik dengan cepat dan efisien. Dalam artikel ini, kita akan memberikan sekilas contoh GDScript untuk memberi Anda gambaran tentang bagaimana bahasa ini bekerja dalam lingkungan Godot.

## Mengenal GDScript

GDScript adalah bahasa pemrograman berbasis skrip yang dikembangkan khusus untuk digunakan dalam Godot Engine. Bahasa ini sangat mirip dengan Python, dengan sintaksis yang mudah dipahami dan dikelola oleh engine. GDScript memiliki dukungan penuh untuk fitur-fitur Godot seperti pemrograman berorientasi objek, sistem sinyal, pengelolaan memori otomatis, dan masih banyak lagi.

## Contoh 1: Menampilkan Pesan pada konsol

Mari kita mulai dengan contoh sederhana yang menunjukkan cara menampilkan pesan pada konsol output menggunakan GDScript di Godot:

```gd

func _ready():
	print("Halo, Dunia!")
```

Dalam contoh ini, fungsi `_ready()` dipanggil saat Node siap digunakan. Pada baris selanjutnya, kita menggunakan metode `print()` untuk mencetak pada layar "Halo, Dunia!". Ketika game dijalankan, pesan ini akan ditampilkan pada layar.

## Contoh 2: Pengendalian Pemain dengan Keyboard

Selanjutnya, mari kita lihat contoh penggunaan GDScript untuk mengendalikan karakter pemain dengan keyboard:

```gd
extends KinematicBody2D

const SPEED = 200
var velocity = Vector2.ZERO

func _process(delta):
	var move_direction = Vector2.ZERO

	if Input.is_action_pressed("ui_right"):
		move_direction.x += 1
	if Input.is_action_pressed("ui_left"):
		move_direction.x -= 1
	if Input.is_action_pressed("ui_down"):
		move_direction.y += 1
	if Input.is_action_pressed("ui_up"):
		move_direction.y -= 1

	velocity = move_direction.normalized() * SPEED
	move_and_slide(velocity)
```

Dalam contoh ini, kita menggunakan skrip GDScript yang terhubung ke Node KinematicBody2D. Pada setiap frame, fungsi `_process(delta)` dipanggil. kita mendapatkan arah pergerakan dari input pemain menggunakan metode `Input.is_action_pressed()` dan mengubahnya menjadi vektor arah `move_direction`. Selanjutnya, kita menghitung kecepatan dengan mengalikan arah pergerakan dengan kecepatan maksimum `SPEED`. Akhirnya, kita menggunakan metode `move_and_slide()` untuk menggerakkan karakter berdasarkan kecepatan.

## Contoh 3: Deteksi Collision Sederhana

Terakhir, mari kita lihat contoh penggunaan GDScript untuk mendeteksi tabrakan antara dua objek:

```gd
extends Area2D

signal collided

func _on_Area2D_body_entered(body):
	if body.name == "Player":
		emit_signal("collided")
```

Dalam contoh ini, kita menggunakan skrip GDScript yang terhubung ke Node Area2D

. Ketika objek ini berinteraksi dengan objek lain yang masuk ke dalam area (body), fungsi `_on_Area2D_body_entered(body)` dipanggil. kita memeriksa apakah objek yang masuk memiliki nama "Player" dan kemudian mengirimkan sinyal "collided" menggunakan metode `emit_signal()`.

## Kesimpulan

Ini hanyalah sekilas contoh GDScript yang menunjukkan beberapa fitur dasar dan potensi dari bahasa ini dalam Godot Game Engine. GDScript sangat fleksibel dan dapat digunakan untuk mengimplementasikan logika game yang kompleks dengan mudah. Kami harap contoh-contoh ini memberikan gambaran awal yang berguna bagi Anda yang baru memulai dengan GDScript.

Selanjutnya, Anda dapat menjelajahi lebih lanjut dokumentasi Godot dan mencoba contoh-contoh proyek yang telah disediakan oleh komunitas untuk memperdalam pemahaman Anda tentang GDScript. Selamat mencoba dan semoga sukses dalam pengembangan game dengan Godot dan GDScript!