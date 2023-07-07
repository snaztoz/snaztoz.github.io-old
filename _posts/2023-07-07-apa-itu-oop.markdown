---
layout: post
title:  "OOP: Apa Itu Object-Oriented Programming?"
date:   2023-07-07 09:57:00 +0700
author: snaztoz
categories: programming
tags: oop python
---

Paradigma *object-oriented programming* atau yang biasa disingkat menjadi OOP adalah sebuah paradigma yang populer digunakan di banyak bahasa pemrograman. Namun, apakah sebenarnya OOP itu?

Jika kita mengunjungi situs Wikipedia untuk membaca informasi tentang beberapa bahasa pemrograman yang paling banyak digunakan saat ini, tidak jarang kita akan menemukan kalimat seperti berikut:

> Java is a high-level, class-based, **object-oriented** programming language... [Java (programming language) - Wikipedia](https://en.wikipedia.org/wiki/Java_(programming_language))

> Python is ... . It supports multiple programming paradigms, including ..., **object-oriented** and ... [Python (programming language) - Wikipedia](https://en.wikipedia.org/wiki/Python_(programming_language))

> Ruby is ... .  It supports multiple programming paradigms, including ..., **object-oriented**, and ... [Ruby (programming language) - Wikipedia](https://en.wikipedia.org/wiki/Ruby_(programming_language))

Bahkan bahasa pemrograman yang kini tengah naik daun beberapa tahun belakangan ini, Golang, juga memiliki sentuhan *object-oriented* di dalamnya.

Jadi mengapa *object-oriented programming* (atau OOP) ini bisa sangat banyak digunakan oleh bahasa-bahasa pemrograman populer di dunia?

Kita akan membahasnya satu-persatu, dimulai dari yang paling awal dulu:

## Pengertian Object

*Object* (seperti namanya), adalah inti utama dari paradigma ini. Oleh karenanya penting untuk kita bisa memahami konsep ini.

Definisi mudah untuk menjelaskan apa itu *object* ialah:
* Sesuatu hal yang memiliki nilai/sifat tertentu; dan
* Sesuatu hal yang memiliki kemampuan tertentu

Apa maksudnya?

Sebagai contoh, mari kita bayangkan ada sebuah mobil yang memiliki cat berwarna merah (sebuah nilai) dan dapat melaju ke depan ataupun mundur ke belakang (sebuah kemampuan).

Maka kita dapat mengatakan bahwa mobil tersebut adalah sebuah *object*!

Contoh lain, bayangkan terdapat seekor kucing yang memiliki bulu lebat (sebuah nilai), dan kucing tersebut dapat meloncat tinggi ke atas pagar (sebuah kemampuan). Maka kucing tersebut juga dapat kita katakan sebagai sebuah *object*.

Konsep ini identikal penggunaannya di banyak bahasa-bahasa pemrograman.

Di dunia pemrograman, nilai/sifat dari sebuah *object* seringkali disebut sebagai **property**, sedangkan kemampuan yang dapat dilakukan *object* seringkali disebut sebagai **method**.

## Pengertian Class

Di sisi lain, banyak di antara bahasa pemrograman yang berparadigma *object-oriented* juga memiliki konsep lain yang bernama *class*. Nah, apa itu *class*?

Mudahnya, *class* adalah sebuah cetakan untuk membuat *object*.

Katakanlah terdapat sebuah mobil sedan sebagai *object*, maka kita dapat menganalogikan *class* sebagai [blueprint](https://en.wikipedia.org/wiki/Blueprint) dari mobil sedan tersebut.

Dengan adanya sebuah *blueprint*, maka pekerja di pabrik-pabrik mobil sedan akan dapat mengetahui cara untuk bisa membuat mobil sedan, berapapun jumlah yang diinginkannya, sesuai dengan spesifikasi yang ada.

Di bahasa Python, kita dapat menerapkan konsep ini seperti berikut:

{% highlight python %}
# Membuat class (blueprint sedan)
class Sedan:
  # Abaikan saja dulu bagian ini jika belum terlalu familiar
  # dengan penggunaan class di Python sebelumnya
  def __init__(self, warna):
    self.warna = warna

  def melaju(arah):
    if arah == 'depan':
      print('Mobil sedan melaju ke depan')
    elif arah == 'belakang':
      print('Mobil sedan mundur ke belakang')


# Sekarang kita bisa membuat berapapun object (sedan) dengan
# menggunakan class yang telah dibuat sebelumnya
sedan_pertama = Sedan('merah')
sedan_pertama.melaju('depan')

sedan_kedua = Sedan('polkadot')
sedan_kedua.melaju('belakang')
sedan_kedua.melaju('depan')

# sedan_ketiga = ...
# blabla = ...
# dst...
{% endhighlight %}

Di bahasa lain seperti Java ataupun Ruby, cara kerja dari *class* dan *object* ini kurang lebih serupa.

Meskipun demikian, di beberapa bahasa lain hal ini belum tentu 100% sama.

Sebagai contoh, meskipun *object* pada Golang (seringkali) juga memiliki *property* dan juga *method*, namun pada bahasa ini tidak ada yang namanya *class*!

Sebagai gantinya, bahasa Golang menggunakan konsep lain yang bernama **struct**. *Struct* ini kurang lebih serupa dengan *class*, namun di beberapa sisi mereka memiliki beberapa perbedaan yang cukup signifikan. Akan terlalu panjang jika perbedaan tersebut kita bahas di postingan ini, jadi mari kita kesampingkan dulu hal ini.

## Pengertian Object-Oriented Programming

Setelah memahami konsep dari *object* dan *class*, kita sudah bisa memperoleh definisi dari *object-oriented programming* itu sendiri.

Mudahnya, *object-oriented programming* atau OOP adalah sebuah paradigma pemrograman yang memusatkan pada penggunaan satu atau lebih *object* untuk merangkai sebuah sistem *software*.

*Object-object* tersebut kemudian dapat berinteraksi satu sama lain sehingga dapat menyusun sebuah sistem yang utuh.

Sebagai contoh, bayangkan pada sebuah *software* yang menyusun website terdapat:
* *object* untuk mengambil data dari database
* *object* untuk mengolah data tersebut
* *object* untuk menampilkan data
* dan seterusnya...

Dengan membagi tugas-tugas tersebut ke dalam *object* yang berbeda, *software* dapat dengan lebih mudah untuk dilakukan *maintenance*, sehingga *bug* yang mungkin terdapat di dalamnya juga akan lebih mudah ditemukan dan lebih sedikit jumlahnya.

## Alternatif

Apakah paradigma OOP merupakan satu-satunya paradigma yang dapat digunakan? Tentu tidak.

Terdapat banyak paradigma pemrograman lain yang dapat digunakan untuk bisa membuat sebuah *software*.

Sebagai contoh, terdapat [paradigma imperatif](https://en.wikipedia.org/wiki/Imperative_programming) yang menggunakan *statement* untuk mengubah *state* dari sebuah program. Digunakan oleh beberapa bahasa, salah satunya yaitu bahasa C.

Lalu ada juga [paradigma fungsional](https://en.wikipedia.org/wiki/Functional_programming) yang menggunakan fungsi-fungsi kecil untuk menyusun sebuah program yang lebih besar. Contoh bahasa yang menggunakan paradigma ini ialah Haskell dan Elixir.

...dan masih banyak lagi paradigma [lainnya](https://en.wikipedia.org/wiki/Programming_paradigm)!

## Kesimpulan

*Object* adalah sesuatu yang memiliki nilai (*property*) dan/atau juga memiliki kemampuan untuk melakukan sesuatu (*method*).

Paradigma *object-oriented programming* (OOP) menggunakan sekumpulan *object* untuk berinteraksi dengan satu sama lain untuk dapat menyusun sebuah sistem yang lebih kompleks.

Paradigma ini sendiri bukanlah satu-satunya paradigma pemrograman yang dapat digunakan untuk membuat sebuah *software*.
