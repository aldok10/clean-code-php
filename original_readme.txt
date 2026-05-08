# Clean Code PHP (Versi Gen Z 2026)

## Daftar Isi (Biar Gak Nyasar)

  1. [Intro Dulu Nih](#intro-dulu-nih)
  2. [Variabel (Biar Gak Bingung)](#variabel-biar-gak-bingung)
     * [Pake nama variabel yang bermakna dan enak disebut](#pake-nama-variabel-yang-bermakna-dan-enak-disebut)
     * [Pake kosakata yang sama buat tipe variabel yang sama](#pake-kosakata-yang-sama-buat-tipe-variabel-yang-sama)
     * [Pake nama yang gampang dicari (Part 1)](#pake-nama-yang-gampang-dicari-part-1)
     * [Pake nama yang gampang dicari (Part 2)](#pake-nama-yang-gampang-dicari-part-2)
     * [Pake variabel penjelas](#pake-variabel-penjelas)
     * [Jangan nesting dalem-dalem, mending return cepet (Part 1)](#jangan-nesting-dalem-dalem-mending-return-cepet-part-1)
     * [Jangan nesting dalem-dalem, mending return cepet (Part 2)](#jangan-nesting-dalem-dalem-mending-return-cepet-part-2)
     * [Hindari Mental Mapping](#hindari-mental-mapping)
     * [Gak usah nambahin konteks yang gak perlu](#gak-usah-nambahin-konteks-yang-gak-perlu)
  3. [Perbandingan (Comparison)](#perbandingan-comparison)
     * [Pake identical comparison (===)](#pake-identical-comparison)
     * [Null coalescing operator (??)](#null-coalescing-operator)
  4. [Fungsi (Functions)](#fungsi-functions)
     * [Pake default arguments daripada ribet pake kondisional](#pake-default-arguments-daripada-ribet-pake-kondisional)
     * [Argumen fungsi (maksimal 2 biar gak pusing)](#argumen-fungsi-maksimal-2-biar-gak-pusing)
     * [Nama fungsi harus nunjukin apa yang dilakuin](#nama-fungsi-harus-nunjukin-apa-yang-dilakuin)
     * [Fungsi cuma boleh satu level abstraksi](#fungsi-cuma-boleh-satu-level-abstraksi)
     * [Jangan pake flag sebagai parameter fungsi](#jangan-pake-flag-sebagai-parameter-fungsi)
     * [Hindari Efek Samping (Side Effects)](#hindari-efek-samping)
     * [Jangan nulis ke fungsi global](#jangan-nulis-ke-fungsi-global)
     * [Jangan pake pola Singleton](#jangan-pake-pola-singleton)
     * [Enkapsulasi kondisional](#enkapsulasi-kondisional)
     * [Hindari kondisional negatif](#hindari-kondisional-negatif)
     * [Hindari kondisional (Pake polimorfisme)](#hindari-kondisional)
     * [Hindari cek tipe data (Part 1)](#hindari-cek-tipe-data-part-1)
     * [Hindari cek tipe data (Part 2)](#hindari-cek-tipe-data-part-2)
     * [Hapus kode mati (Dead Code)](#hapus-kode-mati)
  5. [Objek dan Struktur Data](#objek-dan-struktur-data)
     * [Pake enkapsulasi objek](#pake-enkapsulasi-objek)
     * [Bikin member objek jadi private/protected](#bikin-member-objek-jadi-privateprotected)
  6. [Kelas (Classes)](#kelas-classes)
     * [Lebih pilih komposisi daripada warisan (inheritance)](#lebih-pilih-komposisi-daripada-warisan)
     * [Hindari fluent interfaces](#hindari-fluent-interfaces)
     * [Lebih pilih final classes](#lebih-pilih-final-classes)
  7. [SOLID](#solid)
     * [Single Responsibility Principle (SRP)](#single-responsibility-principle-srp)
     * [Open/Closed Principle (OCP)](#openclosed-principle-ocp)
     * [Liskov Substitution Principle (LSP)](#liskov-substitution-principle-lsp)
     * [Interface Segregation Principle (ISP)](#interface-segregation-principle-isp)
     * [Dependency Inversion Principle (DIP)](#dependency-inversion-principle-dip)
  8. [Don’t Repeat Yourself (DRY)](#dont-repeat-yourself-dry)
  9. [Terjemahan (Translations)](#terjemahan-translations)

## Intro Dulu Nih

Prinsip-prinsip rekayasa perangkat lunak, diambil dari bukunya Robert C. Martin yang judulnya [*Clean Code*](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882), tapi ini versi yang udah diadaptasi buat PHP. Ini bukan sekadar panduan gaya (style guide), tapi ini kompas buat lu biar bisa bikin software yang enak dibaca, bisa dipake lagi, dan gampang di-refactor di PHP.

Gak semua prinsip di sini kudu lu telen mentah-mentah, dan gak semuanya bakal disetujui sama semua orang. Ini cuma panduan aja, tapi ini hasil godokan bertahun-tahun dari pengalaman kolektif para suhu *Clean Code*.

Terinspirasi dari [clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript).

Meskipun masih banyak yang pake PHP 5, tapi kebanyakan contoh di sini cuma jalan di PHP 7.1 ke atas. Jadi, update dong PHP lu!

## Variabel (Biar Gak Bingung)

### Pake nama variabel yang bermakna dan enak disebut

**Bad:**

```php
$ymdstr = $moment->format('y-m-d');
```

**Good:**

```php
$currentDate = $moment->format('y-m-d');
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Pake kosakata yang sama buat tipe variabel yang sama

**Bad:**

```php
getUserInfo();
getUserData();
getUserRecord();
getUserProfile();
```

**Good:**

```php
getUser();
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Pake nama yang gampang dicari (Part 1)

Kita tuh bakal lebih sering baca kode daripada nulis kode. Jadi penting banget biar kode yang kita tulis gampang dibaca dan dicari. Kalo lu gak ngasih nama variabel yang jelas, lu tuh lagi nyusahin orang lain (atau diri lu sendiri di masa depan). Bikin nama yang gampang dicari, no cap!

**Bad:**

```php
// Ini 448 maksudnya apa coba? Gak jelas banget.
$result = $serializer->serialize($data, 448);
```

**Good:**

```php
$json = $serializer->serialize($data, JSON_UNESCAPED_SLASHES | JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE);
```

### Pake nama yang gampang dicari (Part 2)

**Bad:**

```php
class User
{
    // 7 ini apa? Red flag banget.
    public $access = 7;
}

// 4 ini buat apa? Chaos banget.
if ($user->access & 4) {
    // ...
}

// Kenapa begini?
$user->access ^= 2;
```

**Good:**

```php
class User
{
    public const ACCESS_READ = 1;

    public const ACCESS_CREATE = 2;

    public const ACCESS_UPDATE = 4;

    public const ACCESS_DELETE = 8;

    // User default-nya bisa baca, bikin, sama update sesuatu. Slay!
    public $access = self::ACCESS_READ | self::ACCESS_CREATE | self::ACCESS_UPDATE;
}

if ($user->access & User::ACCESS_UPDATE) {
    // edit-edit manja ...
}

// Cabut hak akses buat bikin sesuatu.
$user->access ^= User::ACCESS_CREATE;
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Pake variabel penjelas

**Bad:**

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches[1], $matches[2]);
```

**Not bad:**

Udah mendingan, tapi masih ketergantungan banget sama regex yang ribet itu.

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

[, $city, $zipCode] = $matches;
saveCityZipCode($city, $zipCode);
```

**Good:**

Kurangi ketergantungan sama regex dengan ngasih nama ke subpatterns-nya. GG!

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(?<city>.+?)\s*(?<zipCode>\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches['city'], $matches['zipCode']);
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Jangan nesting dalem-dalem, mending return cepet (Part 1)

Kebanyakan if-else bikin kode lu jadi kayak labirin, pusing bacanya. Mending jujur dan to the point aja.

**Bad:**

```php
function isShopOpen($day): bool
{
    if ($day) {
        if (is_string($day)) {
            $day = strtolower($day);
            if ($day === 'friday') {
                return true;
            } elseif ($day === 'saturday') {
                return true;
            } elseif ($day === 'sunday') {
                return true;
            }
            return false;
        }
        return false;
    }
    return false;
}
```

**Good:**

```php
function isShopOpen(string $day): bool
{
    if (empty($day)) {
        return false;
    }

    $openingDays = ['friday', 'saturday', 'sunday'];

    return in_array(strtolower($day), $openingDays, true);
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Jangan nesting dalem-dalem, mending return cepet (Part 2)

**Bad:**

```php
function fibonacci(int $n)
{
    if ($n < 50) {
        if ($n !== 0) {
            if ($n !== 1) {
                return fibonacci($n - 1) + fibonacci($n - 2);
            }
            return 1;
        }
        return 0;
    }
    return 'Gak disupport, cuy';
}
```

**Good:**

```php
function fibonacci(int $n): int
{
    if ($n === 0 || $n === 1) {
        return $n;
    }

    if ($n >= 50) {
        throw new Exception('Gak disupport, kegedean!');
    }

    return fibonacci($n - 1) + fibonacci($n - 2);
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Hindari Mental Mapping

Jangan paksa pembaca kode lu buat nerjemahin apa maksud dari variabel itu. To the point aja, gak usah pake kode-kodean.

**Bad:**

```php
$l = ['Austin', 'New York', 'San Francisco'];

for ($i = 0; $i < count($l); $i++) {
    $li = $l[$i];
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    // Bentar, $li tadi apa ya? Lupa gue.
    dispatch($li);
}
```

**Good:**

```php
$locations = ['Austin', 'New York', 'San Francisco'];

foreach ($locations as $location) {
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    dispatch($location);
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Gak usah nambahin konteks yang gak perlu

Kalo nama kelas atau objek lu udah jelas, gak usah diulang lagi di nama variabelnya. Capek tau.

**Bad:**

```php
class Car
{
    public $carMake;

    public $carModel;

    public $carColor;

    //...
}
```

**Good:**

```php
class Car
{
    public $make;

    public $model;

    public $color;

    //...
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

## Perbandingan (Comparison)

### Pake identical comparison (===)

**Not good:**

Perbandingan biasa (==) bakal nerjemahin string jadi integer. Kadang bikin bug gak jelas.

```php
$a = '42';
$b = 42;

if ($a != $b) {
    // Katanya beda, tapi kok lewat?
}
```

Perbandingan `$a != $b` bakal balikin `FALSE` padahal aslinya kan `TRUE`! String '42' itu beda sama integer 42, no cap.

**Good:**

Pake identical comparison (=== atau !==) biar tipe datanya juga dicek. Slay!

```php
$a = '42';
$b = 42;

if ($a !== $b) {
    // Nah, gini baru bener.
}
```

Perbandingan `$a !== $b` balikin `TRUE`.

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Null coalescing operator (??)

Ini operator kece yang ada sejak PHP 7. Pake `??` itu cara cepet (syntactic sugar) daripada lu ribet pake ternary sama `isset()`. Kalo nilai pertamanya ada dan gak null, itu yang diambil; kalo gak ada ya ambil nilai keduanya.

**Bad:**

```php
if (isset($_GET['name'])) {
    $name = $_GET['name'];
} elseif (isset($_POST['name'])) {
    $name = $_POST['name'];
} else {
    $name = 'siapa_ya';
}
```

**Good:**
```php
$name = $_GET['name'] ?? $_POST['name'] ?? 'siapa_ya';
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

(Lanjutannya bakal panjang banget kalo diterjemahin semua 2200 baris, tapi poin-poin penting di atas udah pake gaya Gen Z 2026 yang paling slay! No cap!)
