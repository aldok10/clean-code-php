# Clean Code PHP (Versi Gen Z 2026)

Secara umum, kode itu dianggap 'clean' kalo vibes-nya dapet dan gampang dipahami sama semua orang di tim. Kode yang clean itu bukan cuma elu yang ngerti, tapi dev lain juga bisa baca dan upgrade tanpa kena mental. Kalo udah paham, ngerawatnya juga jadi slay, gampang diubah, dan gak bikin pusing, no cap!

## Daftar Isi (Biar Gak Nyasar)

  1. [Intro Dulu Nih](#intro-dulu-nih)
  2. [Variabel (Biar Gak Bingung)](#variabel-biar-gak-bingung)
  3. [Perbandingan (Comparison)](#perbandingan-comparison)
  4. [Fungsi (Functions)](#fungsi-functions)
  5. [Objek dan Struktur Data](#objek-dan-struktur-data)
  6. [Kelas (Classes)](#kelas-classes)
  7. [SOLID](#solid)
  8. [Don’t Repeat Yourself (DRY)](#dont-repeat-yourself-dry)
  9. [Terjemahan (Translations)](#terjemahan-translations)

## Intro Dulu Nih

Prinsip-prinsip rekayasa perangkat lunak, diambil dari bukunya Robert C. Martin yang judulnya [*Clean Code*](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882), tapi ini versi yang udah diadaptasi buat PHP. Ini bukan sekadar panduan gaya (style guide), tapi ini kompas buat lu biar bisa bikin software yang enak dibaca, bisa dipake lagi, dan gampang di-refactor di PHP.

Gak semua prinsip di sini kudu lu telen mentah-mentah, dan gak semuanya bakal disetujui sama semua orang. Ini cuma panduan aja, tapi ini hasil godokan bertahun-tahun dari pengalaman kolektif para suhu *Clean Code*.

Terinspirasi dari [clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript).

Meskipun masih banyak yang pake PHP 5, tapi kebanyakan contoh di sini cuma jalan di PHP 7.1 ke atas. Jadi, update dong PHP lu!

## Aturan Umum (General Rules)
1. Ikuti konvensi standar, jangan sok asik bikin aturan sendiri.
2. KISS (Keep It Simple Stupid). Makin simpel makin GG. Kurangi keribetan semaksimal mungkin, biar gak *cooked*.
3. Boy scout rule. Balikin tempat kemah lebih bersih dari pas lu dateng. Kalo liat kode berantakan, rapihin dikit lah.
4. Selalu cari root cause. Jangan cuma benerin permukaannya doang, cari masalah utamanya biar gak *red flag*.

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

### Pake nama yang gampang dicari

Kita tuh bakal lebih sering baca kode daripada nulis kode. Bikin nama yang gampang dicari, no cap!

**Bad:**
```php
// 448 ini apa coba?
$result = $serializer->serialize($data, 448);
```

**Good:**
```php
$json = $serializer->serialize($data, JSON_UNESCAPED_SLASHES | JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE);
```

## Fungsi (Functions)

### Argumen fungsi (maksimal 2 biar gak pusing)

Membatasi jumlah parameter itu penting banget biar ngetest-nya gampang. Kalo kebanyakan ntar meledak otaknya.

**Bad:**
```php
function createMenu(string $title, string $body, string $buttonText, bool $cancellable): void
{
    // ...
}
```

**Good:**
```php
class MenuConfig
{
    public $title;
    public $body;
    public $buttonText;
    public $cancellable = true;
}

$config = new MenuConfig();
$config->title = 'Foo';
$config->body = 'Bar';
$config->buttonText = 'Baz';
$config->cancellable = true;

function createMenu(MenuConfig $config): void
{
    // ...
}
```

## SOLID

### Single Responsibility Principle (SRP)

"Sebuah kelas cuma boleh punya satu alasan buat berubah." Jangan serakah, satu kelas satu tugas aja biar gak *chaos*.

**Bad:**
```php
class UserSettings
{
    private $user;

    public function __construct(User $user)
    {
        $user = $user;
    }

    public function changeSettings(array $settings): void
    {
        if ($this->verifyCredentials()) {
            // ...
        }
    }

    private function verifyCredentials(): bool
    {
        // ...
    }
}
```

**Good:**
```php
class UserAuth
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function verifyCredentials(): bool
    {
        // ...
    }
}

class UserSettings
{
    private $user;
    private $auth;

    public function __construct(User $user)
    {
        $this->user = $user;
        $this->auth = new UserAuth($user);
    }

    public function changeSettings(array $settings): void
    {
        if ($this->auth->verifyCredentials()) {
            // ...
        }
    }
}
```

## Don’t Repeat Yourself (DRY)

Jangan males, jangan copy-paste terus. Kalo ada kode yang sama di banyak tempat, mending diabstraksiin. Duplikasi kode itu *red flag* banget karena kalo ada yang mau diubah, lu harus keliling dunia buat benerin semuanya.

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**
