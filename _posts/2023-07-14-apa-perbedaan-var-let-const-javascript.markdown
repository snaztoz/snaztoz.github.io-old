---
layout: post
title:  "Deklarasi Variabel: Apa Perbedaan Var, Let dan Const pada JavaScript?"
date:   2023-07-14 00:00:00 +0700
author: snaztoz
categories: programming
tags: javascript
---

Variabel merupakan salah satu fitur utama dari bahasa pemrograman, termasuk juga JavaScript. Namun, JavaScript memiliki beberapa metode yang dapat digunakan untuk membuat sebuah variabel. Apakah perbedaannya? Metode mana yang lebih baik untuk digunakan?

### Daftar Isi
{:.no_toc}

1. TOC
{:toc}

## Variabel di JavaScript

Variabel merupakan wadah yang dapat digunakan untuk menampung berbagai macam nilai, seperti jumlah siswa, harga sebuah barang di toko swalayan, hingga teks panjang seperti satu bab novel Laskar Pelangi karangan *Andrea Hirata*.

Di dunia *programming*, konsep ini sangatlah penting adanya. Dengan menggunakan variabel, kita tidak perlu menuliskan berulang-ulang, melakukan *copy-paste* setiap 3 blok kode sekali paragraf panjang dari novel Laskar Pelangi tadi.

JavaScript sendiri juga memungkinkan *programmer* untuk menggunakan fitur variabel ini, dengan cara seperti berikut:

{% highlight javascript %}
var nama = "snaztoz"

// atau
let nama = "snaztoz"

// atau bisa juga
const nama = "snaztoz"
{% endhighlight %}

>*"loh, kok ada 3? Bedanya apa?"*

Ketiga cara dalam melakukan pendeklarasian variabel seperti di atas, meskipun pada akhirnya menghasilkan sesuatu yang (dalam kasus ini) kurang lebih sama, masing-masing memiliki hal yang membuat mereka berbeda antara satu dengan yang lain.

Mari kita bahas satu persatu:

## Deklarasi Menggunakan *var*

Metode pertama yang dapat kita gunakan adalah dengan menggunakan *keyword* `var`.

Sifat dari variabel yang dibuat melalui *keyword* ini ialah bersifat *mutable*, dan secara otomatis akan memiliki *scope* dari fungsi terdekat atau *scope* global.

Mari kita lihat contoh berikut:

{% highlight javascript %}
var nama = "snaztoz"

if (nama == "snaztoz") {
  var umur = 22
}

console.log(umur)

// OUTPUT: 22
{% endhighlight %}

Dapat kita lihat, variabel `umur` yang dibuat di dalam blok `if-statement` masih dapat kita akses meskipun alur program sudah keluar dari blok tersebut.

Tentunya untuk sebagian orang yang telah terbiasa dengan bahasa pemrograman lain, sebagai contoh bahasa Java, akan kebingungan dengan perilaku ini. Normalnya jika variabel dibuat di dalam sebuah blok, maka otomatis variabel akan memiliki *scope* dari blok tersebut.

Untuk mengatasi hal ini, pada JavaScript versi ES6 ke atas telah ditambahkan *keyword* baru, yakni `let` *keyword*.

## Deklarasi Menggunakan *let*

Seperti yang telah disebutkan sebelumnya, *keyword* `let` ada untuk melakukan perbaikan atas kekurangan yang ada pada *keyword* `var`.

Sifat yang dimiliki oleh *keyword* ini sama dengan yang dimiliki `var` dalam hal *mutability*, hanya saja perbedaan ada pada *scope* dari variabel yang telah dibuat.

Berikut adalah contoh penggunaan dari variabel ini:

{% highlight javascript %}
if (true) {
  let nama = "snaztoz"
}

console.log(nama)

// OUTPUT: ReferenceError: nama is not defined
{% endhighlight %}

Hasil ketika program di atas dijalankan yakni program akan menghasilkan error ketika melakukan `console.log`, hal ini dikarenakan variabel nama tidak lagi dapat diakses setelah keluar dari dalam blok `if-statement` tersebut.

Perilaku ini sesuai dengan yang menjadi ekspektasi dari banyak orang: yakni variabel hanya akan memiliki *scope* sesuai dari blok dimana ia dideklarasikan.

## Deklarasi Menggunakan *const*

Terakhir, ada cara terakhir untuk melakukan pendeklarasian *variabel*, yakni dengan menggunakan *keyword* `const`.

Berbeda dari `var` dan `let`, variabel yang dibuat melalui *keyword* `const` ini tidak akan dapat dilakukan *assignment* kembali setelah variabel dideklarasikan pertama kali.

Sebagai contoh:

{% highlight javascript %}
const nama = "snaztoz"

// kita melakukan re-assignment
nama = "Hafidh MS"

console.log(nama)

// OUTPUT: TypeError: Assignment to constant variable.
{% endhighlight %}

Ketika kita melakukan *re-assignment*, program akan mengeluarkan error karena hal tersebut tidak diperbolehkan pada variabel yang dibuat dengan cara ini.

Untuk *scope* dari variabel `const` sendiri bersifat sama dengan variabel yang dibuat melalui *keyword* `let`, yakni *block-scoped*.

## TL;DR, Lebih Baik Gunakan yang Mana?

Dari perbedaan-perbedaan yang telah dijelaskan sebelumnya, mungkin kita akan bertanya-tanya "lebih baik menggunakan metode yang mana?"

Saya pribadi, memiliki preferensi seperti berikut:

> 1. Secara default gunakan `const` untuk membuat variabel
> 2. Jika variabel ingin agar bisa diubah-ubah valuenya, gunakan `let`
> 3. Lupakan `var`

Mengapa menggunakan `const` sebagai pilihan utama?

Pola yang secara pribadi sering saya temukan selama ini, sebenarnya kebanyakan variabel tidak membutuhkan perubahan *value* yang ditampungnya. Seringkali dia hanya bertugas untuk menampung sebuah nilai yang tetap sepanjang masa hidup *scope*-nya. Oleh karena itu, `const` tepat untuk digunakan.

Lalu untuk variabel yang memang butuh untuk diubah-ubah *value*-nya, saya lebih memilih menggunakan `let` ketimbang `var` untuk alasan yang telah disebutkan sebelumnya. Alasan untuk memilih `var` hampir atau bahkan tidak ada sama sekali kecuali dalam kasus-kasus khusus seperti untuk menunjang *support* dari browser lama.

### Referensi
{:.no_toc}

* [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
* [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)
* [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const#specifications](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const#specifications)
* [ES6 In Depth: let and const](https://hacks.mozilla.org/2015/07/es6-in-depth-let-and-const/)
