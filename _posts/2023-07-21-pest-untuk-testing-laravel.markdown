---
layout: post
title: "Pest: Test Aplikasi Laravel Dengan Lebih Elegan"
date:   2023-07-21 00:00:01 +0700
author: snaztoz
categories: programming
tags: laravel php testing
---

Laravel memiliki *support* bawaan untuk dapat melakukan testing dengan menggunakan PHPUnit. Ya, pilihan ini memang dapat bekerja dengan baik. Namun, kita bisa juga meng-*upgrade* *developer-experience* (DX) dengan menggunakan Pest sebagai pilihan alternatif dari PHPUnit.

### Daftar Isi
{:.no_toc}

* TOC
{:toc}

## Perkenalan

Testing merupakan sebuah proses yang tidak dapat ditinggalkan untuk dapat membuat sebuah *software* yang berkualitas, tidak terkecuali pada *web-app* yang dibuat dengan menggunakan *framework* seperti Laravel.

Secara default, Laravel menggunakan [PHPUnit](https://phpunit.de/) sebagai *testing framework* bawaannya. Namun, kita bisa juga menggunakan [Pest](https://pestphp.com/) sebagai pilihan alternatif.

Pest sendiri merupakan sebuah *testing framework* yang dibangun di atas PHPUnit dan memiliki API yang terinspirasi oleh [RSpec](https://rspec.info/) ataupun [Jest](https://jestjs.io/), sehingga test secara desain akan dapat terlihat lebih ringkas dan lebih mudah untuk dibaca.

Untuk mulai menggunakan Pest, kita **tidak perlu mengubah** semua test PHPUnit yang sudah kita buat sebelumnya. Hal ini dimungkinkan karena Pest sendiri yang bersifat progresif, sehingga perubahan dapat dilakukan sedikit demi sedikit.

## Hal-hal yang Perlu Dipersiapkan

Pada artikel ini, saya menggunakan **PHP 8.2** dan juga **Composer 2.5**.

Untuk *text-editor* sendiri, saya menggunakan VSCode (ya, *editor* lain pun tidak menjadi masalah).

## Instalasi

Sebelum memulai, pastikan bahwa [hal-hal yang diperlukan](#hal-hal-yang-perlu-dipersiapkan) untuk mengikuti tutorial ini sudah terinstall.

Langkah pertama, install Laravel (pada artikel ini **Laravel 10**) dengan menggunakan Composer:

{% highlight shell %}
composer create-project laravel/laravel my-pest-project

# ...tunggu hingga selesai...

cd my-pest-project && code .
{% endhighlight %}

Selanjutnya, install Pest dan plugin yang diperlukan:

{% highlight shell %}
composer require pestphp/pest pestphp/pest-plugin-laravel --dev --with-all-dependencies
{% endhighlight %}

Setelah berhasil ter-install, kita perlu melakukan inisialisasi konfigurasi Pest:

{% highlight shell %}
./vendor/bin/pest --init
{% endhighlight %}

Setelah konfigurasi selesai, sebuah file baru bernama `Pest.php` akan terbuat secara otomatis di dalam *directory* `tests/`.

Terakhir, mari kita periksa apakah Pest berhasil dijalankan atau tidak:

{% highlight shell %}
./vendor/bin/pest
{% endhighlight %}

Jika tidak ada error, maka Pest siap untuk digunakan!

## Menulis Kode MathService

Sebagai demonstrasi, mari kita membuat sebuah *class* baru yang bernama `MathService`.

Di dalam *directory* `app/`, buat sebuah *directory* baru yang kita beri nama `Services/`. Selanjutnya, di dalam *directory* tersebut, buat sebuah file baru yang bernama `MathService.php`. Sehingga struktur *directory* `app/` akan terlihat seperti ini:

![Struktur Directory](/assets/images/pest-untuk-testing-laravel/directory-structure.png)

Setelah itu, salin kode berikut ke dalam *file* `MathService.php`:

{% highlight php %}
<?php

namespace App\Services;

class MathService
{
    /**
     * Menambahkan bilangan $number dengan 5
     */
    public static function addWithFive(int $number): int
    {
        return $number + 2;
    }
}
{% endhighlight %}

## Membuat Test untuk MathService

Untuk memastikan apakah kode yang dibuat sebelumnya telah bekerja dengan benar, kita perlu membuat test untuk kode tersebut.

Jalankan perintah berikut untuk membuat sebuah *file* test baru:

{% highlight shell %}
php artisan make:test MathServiceTest --pest
{% endhighlight %}

Perintah tersebut akan membuat sebuah *file* baru bernama `MathServiceTest.php` di dalam *directory* `tests/Feature/`.

Salin kode berikut ke dalam *file* `MathServiceTest.php`:

{% highlight php %}
<?php

namespace Tests\Feature;

use App\Services\MathService;

test('add with five', function () {
    $result = MathService::addWithFive(10);

    expect($result)->toBe(15);
});
{% endhighlight %}

Setelah selesai membuat test untuk `MathService`, mari kita jalankan test.

Test yang ditulis dengan menggunakan Pest juga dapat dijalankan dengan menggunakan perintah test bawaan dari Laravel, yakni dengan menggunakan perintah `artisan` berikut:

{% highlight shell %}
php artisan test
{% endhighlight %}

Test yang dijalankan akan menghasilkan tampilan error seperti yang ada di bawah ini pada *console*:

![Test Error](/assets/images/pest-untuk-testing-laravel/test-error.png)

Saatnya *bug-hunting*!

## Fix Kode MathService

Pada tampilan error sebelumnya, kita mendapatkan sebuah pesan:

> Failed asserting that 12 is identical to 15.

Kemudian jika kita membuka file `MathService.php`, kita akan menemukan sebuah kesalahan pada *method* `addWithFive`, dimana kita menambahkan bilangan `$number` dengan `2`, dan bukan `5`.

Mari kita perbaiki kode pada *method* tersebut:

{% highlight php %}
// ...

class MathService
{
    /**
     * Menambahkan bilangan $number dengan 5
     */
    public static function addWithFive(int $number): int
    {
        return $number + 5;
    }
}
{% endhighlight %}

Sekarang kita jalankan kembali test:

{% highlight shell %}
php artisan test
{% endhighlight %}

Hasil yang ditampilkan pada *console* kali ini adalah:

![Test Error](/assets/images/pest-untuk-testing-laravel/test-success.png)

Sekarang semua test telah berhasil *pass*!

## Kesimpulan

Sebelumnya, kita telah berhasil menulis sebuah test pada aplikasi Laravel dengan menggunakan *framework* Pest.

Seperti yang dapat dilihat, kita tidak perlu membuang test-test PHPUnit yang ada terlebih dulu. Hal ini dapat dilakukan karena sifat progresif dari Pest itu sendiri.

### Pest vs Framework Lain

Test yang ditulis dengan Pest sendiri terlihat lebih bersih dan ringkas jika dibandingkan dengan PHPUnit. Berikut adalah perbandingan dari keduanya untuk sebuah test yang sama:

![With Pest](/assets/images/pest-untuk-testing-laravel/test-with-pest.png)

![With PHPUnit](/assets/images/pest-untuk-testing-laravel/test-with-phpunit.png)

Tentunya hal ini juga bergantung kepada selera dan keputusan dari masing-masing tim untuk memilih *framework* yang mana untuk digunakan pada sebuah project.

Jika dibandingkan dengan *framework* pada bahasa lain seperti RSpec ataupun Jest, Pest masih memiliki kekurangan, seperti tidak (atau belum) adanya *support* untuk melakukan *grouping* test dengan menggunakan blok `describe` (lihat *issue* ini: [https://github.com/pestphp/pest/issues/15](https://github.com/pestphp/pest/issues/15)).

Meskipun demikian, saya pribadi menyukai tingkat ke-ekspresifan yang ditawarkan oleh *framework* ini jika dibandingkan dengan PHPUnit dan tertarik untuk menggunakannya lagi di project-project mendatang.
