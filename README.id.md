# Clean Code PHP (Versi Gen Z 2026)

Secara umum, kode itu dianggap 'clean' kalo vibes-nya dapet dan gampang dipahami sama semua orang di tim. Kode yang clean itu bukan cuma elu yang ngerti, tapi dev lain juga bisa baca dan upgrade tanpa kena mental. Kalo udah paham, ngerawatnya juga jadi slay, gampang diubah, dan gak bikin pusing, no cap!

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
     * [Ekspresi Match (PHP 8.0+)](#ekspresi-match-php-80)
  4. [Fungsi (Functions)](#fungsi-functions)
     * [Pake default arguments daripada ribet pake kondisional](#pake-default-arguments-daripada-ribet-pake-kondisional)
     * [Argumen fungsi (maksimal 2 biar gak pusing)](#argumen-fungsi-maksimal-2-biar-gak-pusing)
     * [Constructor Property Promotion (PHP 8.0+)](#constructor-property-promotion-php-80)
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
     * [Property Hooks & Asymmetric Visibility (PHP 8.4+)](#property-hooks--asymmetric-visibility-php-84)
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

Meskipun masih banyak yang pake PHP 5, tapi kebanyakan contoh di sini cuma jalan di PHP 8.4 ke atas. Jadi, update dong PHP lu!

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

Kita tuh bakal lebih sering baca kode daripada nulis kode. Jadi penting banget biar kode yang kita tulis gampang dibaca dan dicari. Bikin nama yang gampang dicari, no cap!

**Bad:**
```php
// 448 ini apa coba? Gak jelas banget.
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

**Good:**
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
}
```

**Good:**
```php
class Car
{
    public $make;
    public $model;
    public $color;
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

## Perbandingan (Comparison)

### Pake identical comparison (===)

**Bad:**
```php
$a = '42';
$b = 42;

if ($a != $b) {
    // Katanya beda, tapi kok lewat?
}
```

**Good:**
```php
$a = '42';
$b = 42;

if ($a !== $b) {
    // Nah, gini baru bener.
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Null coalescing operator (??)

### Ekspresi Match (PHP 8.0+)

Kalo lu punya banyak kondisi, mending pake `match` daripada `switch`. Lebih ringkas, lebih aman, dan gak perlu pake `break` yang bikin ribet. Slay banget!

**Bad:**
```php
switch ($status) {
    case 200:
        $message = 'OK';
        break;
    case 404:
        $message = 'Not Found';
        break;
    case 500:
        $message = 'Internal Server Error';
        break;
    default:
        $message = 'Unknown Status';
        break;
}
```

**Good:**
```php
$message = match ($status) {
    200 => 'OK',
    404 => 'Not Found',
    500 => 'Internal Server Error',
    default => 'Unknown Status',
};
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

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

## Fungsi (Functions)

### Pake default arguments daripada ribet pake kondisional

**Bad:**
```php
function createMicrobrewery($breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**Good:**
```php
function createMicrobrewery(string $breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Argumen fungsi (maksimal 2 biar gak pusing)

### Constructor Property Promotion (PHP 8.0+)

Gak perlu deklarasi variabel berkali-kali di kelas. Langsung aja di constructor, biar kode lu makin GG dan ringkas.

**Bad:**
```php
class User
{
    public string $name;
    public string $email;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }
}
```

**Good:**
```php
class User
{
    public function __construct(
        public string $name,
        public string $email,
    ) {}
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

**Bad:**
```php
class Questionnaire
{
    public function __construct(
        string $firstname,
        string $lastname,
        string $patronymic,
        string $region,
        string $district,
        string $city,
        string $phone,
        string $email
    ) {
        // ...
    }
}
```

**Good:**
```php
class ContactData
{
    public $firstname;
    public $lastname;
    public $patronymic;
    public $region;
    public $district;
    public $city;
    public $phone;
    public $email;

    public function __construct(string $firstname, string $lastname, string $phone)
    {
        $this->firstname = $firstname;
        $this->lastname = $lastname;
        $this->phone = $phone;
    }
}

class Questionnaire
{
    public function __construct(ContactData $data)
    {
        // ...
    }
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Nama fungsi harus nunjukin apa yang dilakuin

**Bad:**
```php
function addToDate($date, $month): void
{
    // ...
}

$date = new DateTime();

// Susah nebak ini nambahin apa
addToDate($date, 1);
```

**Good:**
```php
function addMonthToDate(int $month, DateTime $date): void
{
    // ...
}

$date = new DateTime();
addMonthToDate(1, $date);
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Fungsi cuma boleh satu level abstraksi

**Bad:**
```php
function parseBetterPHPCode(string $code): void
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            // ...
        }
    }

    foreach ($tokens as $token) {
        // level abstraksi rendah
    }
}
```

**Good:**
```php
function tokenize(string $code): array
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            $tokens[] = /* ... */;
        }
    }

    return $tokens;
}

function lexer(array $tokens): void
{
    foreach ($tokens as $token) {
        // level abstraksi rendah
    }
}

function parseBetterPHPCode(string $code): void
{
    $tokens = tokenize($code);
    lexer($tokens);
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Jangan pake flag sebagai parameter fungsi

**Bad:**
```php
function createFile(string $name, bool $temp = false): void
{
    if ($temp) {
        touch('./temp/'.$name);
    } else {
        touch($name);
    }
}
```

**Good:**
```php
function createFile(string $name): void
{
    touch($name);
}

function createTempFile(string $name): void
{
    touch('./temp/'.$name);
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Hindari Efek Samping (Side Effects)

**Bad:**
```php
// Variabel global dipake fungsi. Red flag!
$name = 'Ryan McDermott';

function splitNameByFullname(): void
{
    global $name;
    $name = explode(' ', $name);
}

splitNameByFullname();

var_dump($name); // ['Ryan', 'McDermott']
```

**Good:**
```php
function splitName(string $name): array
{
    return explode(' ', $name);
}

$name = 'Ryan McDermott';
$newName = splitName($name);

var_dump($name); // 'Ryan McDermott'
var_dump($newName); // ['Ryan', 'McDermott']
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Jangan nulis ke fungsi global

**Bad:**
```php
function config(): array
{
    return  [
        'foo' => 'bar',
    ];
}
```

**Good:**
```php
class Configuration
{
    private $configuration = [];

    public function __construct(array $configuration)
    {
        $this->configuration = $configuration;
    }

    public function get(string $key): ?string
    {
        return $this->configuration[$key] ?? null;
    }
}

$configuration = new Configuration([
    'foo' => 'bar',
]);
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Jangan pake pola Singleton

**Bad:**
```php
class DBConnection
{
    private static $instance;

    private function __construct(string $dsn)
    {
        // ...
    }

    public static function getInstance(): self
    {
        if (self::$instance === null) {
            self::$instance = new self('sqlite::memory:');
        }

        return self::$instance;
    }

    // ...
}

$singleton = DBConnection::getInstance();
```

**Good:**
```php
class DBConnection
{
    public function __construct(string $dsn)
    {
        // ...
    }

    // ...
}

$connection = new DBConnection('sqlite::memory:');
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Enkapsulasi kondisional

**Bad:**
```php
if ($article->state === 'published') {
    // ...
}
```

**Good:**
```php
if ($article->isPublished()) {
    // ...
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Hindari kondisional negatif

**Bad:**
```php
if (!$node->isNotRoot()) {
    // ...
}
```

**Good:**
```php
if ($node->isRoot()) {
    // ...
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Hindari kondisional (Pake polimorfisme)

**Bad:**
```php
class Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        switch ($this->type) {
            case '777':
                return $this->getMaxAltitude() - $this->getPassengerCount();
            case 'Air Force One':
                return $this->getMaxAltitude();
            case 'Cessna':
                return $this->getMaxAltitude() - $this->getFuelExpenditure();
        }
    }
}
```

**Good:**
```php
interface Airplane
{
    // ...

    public function getCruisingAltitude(): int;
}

class Boeing777 implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getPassengerCount();
    }
}

class AirForceOne implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude();
    }
}

class Cessna implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getFuelExpenditure();
    }
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Hindari cek tipe data (Part 1)

**Bad:**
```php
function travelToTexas($vehicle): void
{
    if ($vehicle instanceof Bicycle) {
        $vehicle->pedal($this->currentLocation, new Location('texas'));
    } elseif ($vehicle instanceof Car) {
        $vehicle->drive($this->currentLocation, new Location('texas'));
    }
}
```

**Good:**
```php
function travelToTexas(Vehicle $vehicle): void
{
    $vehicle->move($this->currentLocation, new Location('texas'));
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Hindari cek tipe data (Part 2)

**Bad:**
```php
function combine($val1, $val2): int
{
    if (!is_numeric($val1) || !is_numeric($val2)) {
        throw new Exception('Must be numbers');
    }

    return $val1 + $val2;
}
```

**Good:**
```php
function combine(int $val1, int $val2): int
{
    return $val1 + $val2;
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Hapus kode mati (Dead Code)

**Bad:**
```php
function oldRequestModule(string $url): void
{
    // ...
}

function newRequestModule(string $url): void
{
    // ...
}

$request = newRequestModule($url);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

**Good:**
```php
function newRequestModule(string $url): void
{
    // ...
}

$request = newRequestModule($url);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

## Objek dan Struktur Data

### Pake enkapsulasi objek

**Bad:**
```php
class Employee
{
    public $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }
}

$employee = new Employee('John Doe');
echo $employee->name; // John Doe
```

**Good:**
```php
class Employee
{
    private $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    public function getName(): string
    {
        return $this->name;
    }
}

$employee = new Employee('John Doe');
echo $employee->getName(); // John Doe
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Bikin member objek jadi private/protected

### Property Hooks & Asymmetric Visibility (PHP 8.4+)

Nah ini fitur paling baru dan paling slay! Lu bisa kontrol akses baca/tulis variabel langsung tanpa perlu ribet bikin getter/setter manual. Bisa pake `public private(set)` juga biar cuma bisa diubah di dalem kelas.

**Bad:**
```php
class User
{
    private string $name;

    public function getName(): string
    {
        return ucfirst($this->name);
    }

    public function setName(string $name): void
    {
        $this->name = trim($name);
    }
}
```

**Good:**
```php
class User
{
    public string $name {
        get => ucfirst($this->name);
        set => trim($value);
    }

    // Cuma bisa dibaca dari luar, tapi cuma bisa di-set dari dalem. GG!
    public private(set) string $email;
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

**Bad:**
```php
class BankAccount
{
    public $balance = 1000;
}

$bankAccount = new BankAccount();

// Beli sepatu...
$bankAccount->balance -= 100;
```

**Good:**
```php
class BankAccount
{
    private $balance;

    public function __construct(int $balance = 1000)
    {
        $this->balance = $balance;
    }

    public function withdraw(int $amount): void
    {
        if ($amount > $this->balance) {
            throw new \Exception('Saldo gak cukup, cuy');
        }

        $this->balance -= $amount;
    }

    public function deposit(int $amount): void
    {
        $this->balance += $amount;
    }

    public function getBalance(): int
    {
        return $this->balance;
    }
}

$bankAccount = new BankAccount();

// Beli sepatu...
$bankAccount->withdraw(100);

echo $bankAccount->getBalance(); // 900
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

## Kelas (Classes)

### Lebih pilih komposisi daripada warisan (inheritance)

**Bad:**
```php
class Employee
{
    private $name;
    private $email;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    // ...
}

// Gak oke karena TaxData itu bukan Employee.
class EmployeeTaxData extends Employee
{
    private $ssn;
    private $salary;

    public function __construct(string $name, string $email, string $ssn, float $salary)
    {
        parent::__construct($name, $email);

        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}
```

**Good:**
```php
class EmployeeTaxData
{
    private $ssn;
    private $salary;

    public function __construct(string $ssn, float $salary)
    {
        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}

class Employee
{
    private $name;
    private $email;
    private $taxData;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    public function setTaxData(EmployeeTaxData $taxData): void
    {
        $this->taxData = $taxData;
    }

    // ...
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Hindari fluent interfaces

**Bad:**
```php
class Car
{
    private $make;
    private $model;
    private $color;

    public function setMake(string $make): self
    {
        $this->make = $make;
        return $this;
    }

    public function setModel(string $model): self
    {
        $this->model = $model;
        return $this;
    }

    public function setColor(string $color): self
    {
        $this->color = $color;
        return $this;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = (new Car())
  ->setColor('pink')
  ->setMake('Ford')
  ->setModel('F-150')
  ->dump();
```

**Good:**
```php
class Car
{
    private $make;
    private $model;
    private $color;

    public function __construct(string $make, string $model, string $color)
    {
        $this->make = $make;
        $this->model = $model;
        $this->color = $color;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = new Car('Ford', 'F-150', 'pink');
$car->dump();
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Lebih pilih final classes

**Bad:**
```php
class City
{
    private $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    public function getName(): string
    {
        return $this->name;
    }
}
```

**Good:**
```php
final class City
{
    private $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    public function getName(): string
    {
        return $this->name;
    }
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

## SOLID

### Single Responsibility Principle (SRP)

**Bad:**
```php
class UserSettings
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
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

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Open/Closed Principle (OCP)

**Bad:**
```php
class AjaxAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'ajaxAdapter';
    }
}

class NodeAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'nodeAdapter';
    }
}

class HttpMailer
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function send(string $message): void
    {
        if ($this->adapter->name === 'ajaxAdapter') {
            $this->adapter->request($message);
        } elseif ($this->adapter->name === 'nodeAdapter') {
            $this->adapter->request($message);
        }
    }
}
```

**Good:**
```php
interface Adapter
{
    public function request(string $message): void;
}

class AjaxAdapter implements Adapter
{
    public function request(string $message): void
    {
        // ...
    }
}

class NodeAdapter implements Adapter
{
    public function request(string $message): void
    {
        // ...
    }
}

class HttpMailer
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function send(string $message): void
    {
        $this->adapter->request($message);
    }
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Liskov Substitution Principle (LSP)

**Bad:**
```php
class Rectangle
{
    protected $width = 0;
    protected $height = 0;

    public function setWidth(int $width): void
    {
        $this->width = $width;
    }

    public function setHeight(int $height): void
    {
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square extends Rectangle
{
    public function setWidth(int $width): void
    {
        $this->width = $this->height = $width;
    }

    public function setHeight(int $height): void
    {
        $this->width = $this->height = $height;
    }
}

function printArea(Rectangle $rectangle): void
{
    $rectangle->setWidth(4);
    $rectangle->setHeight(5);

    // BAD: Bakal balikin 25 buat Square. Harusnya 20.
    echo sprintf('%s has area %d.', get_class($rectangle), $rectangle->getArea()) . PHP_EOL;
}

$rectangles = [new Rectangle(), new Square()];

foreach ($rectangles as $rectangle) {
    printArea($rectangle);
}
```

**Good:**
```php
interface Shape
{
    public function getArea(): int;
}

class Rectangle implements Shape
{
    private $width = 0;
    private $height = 0;

    public function __construct(int $width, int $height)
    {
        $this->width = $width;
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square implements Shape
{
    private $length = 0;

    public function __construct(int $length)
    {
        $this->length = $length;
    }

    public function getArea(): int
    {
        return $this->length ** 2;
    }
}

function printArea(Shape $shape): void
{
    echo sprintf('%s has area %d.', get_class($shape), $shape->getArea()).PHP_EOL;
}

$shapes = [new Rectangle(4, 5), new Square(5)];

foreach ($shapes as $shape) {
    printArea($shape);
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Interface Segregation Principle (ISP)

**Bad:**
```php
interface Employee
{
    public function work(): void;
    public function eat(): void;
}

class HumanEmployee implements Employee
{
    public function work(): void { /* ... */ }
    public function eat(): void { /* ... */ }
}

class RobotEmployee implements Employee
{
    public function work(): void { /* ... */ }
    public function eat(): void { /* Robot gak makan, tapi terpaksa implement. Chaos! */ }
}
```

**Good:**
```php
interface Workable
{
    public function work(): void;
}

interface Feedable
{
    public function eat(): void;
}

interface Employee extends Feedable, Workable
{
}

class HumanEmployee implements Employee
{
    public function work(): void { /* ... */ }
    public function eat(): void { /* ... */ }
}

class RobotEmployee implements Workable
{
    public function work(): void { /* ... */ }
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

### Dependency Inversion Principle (DIP)

**Bad:**
```php
class Employee
{
    public function work(): void { /* ... */ }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

**Good:**
```php
interface Employee
{
    public function work(): void;
}

class Human implements Employee
{
    public function work(): void { /* ... */ }
}

class Robot implements Employee
{
    public function work(): void { /* ... */ }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

## Don’t repeat yourself (DRY)

Jangan males, jangan copy-paste terus. Kalo ada kode yang sama di banyak tempat, mending diabstraksiin. Duplikasi kode itu *red flag* banget karena kalo ada yang mau diubah, lu harus keliling dunia buat benerin semuanya. Slay!

**Bad:**
```php
function showDeveloperList(array $developers): void
{
    foreach ($developers as $developer) {
        $expectedSalary = $developer->calculateExpectedSalary();
        $experience = $developer->getExperience();
        $githubLink = $developer->getGithubLink();
        $data = [$expectedSalary, $experience, $githubLink];

        render($data);
    }
}

function showManagerList(array $managers): void
{
    foreach ($managers as $manager) {
        $expectedSalary = $manager->calculateExpectedSalary();
        $experience = $manager->getExperience();
        $githubLink = $manager->getGithubLink();
        $data = [$expectedSalary, $experience, $githubLink];

        render($data);
    }
}
```

**Good:**
```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        render([
            $employee->calculateExpectedSalary(),
            $employee->getExperience(),
            $employee->getGithubLink()
        ]);
    }
}
```

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**

## Terjemahan (Translations)

Dersedia juga dalam bahasa lain, cuy:

* :cn: **Chinese:** [php-cpm/clean-code-php](https://github.com/php-cpm/clean-code-php)
* :ru: **Russian:** [peter-gribanov/clean-code-php](https://github.com/peter-gribanov/clean-code-php)
* :es: **Spanish:** [fikoborquez/clean-code-php](https://github.com/fikoborquez/clean-code-php)
* :brazil: **Portuguese:** [fabioars/clean-code-php](https://github.com/fabioars/clean-code-php)
* :thailand: **Thai:** [panuwizzle/clean-code-php](https://github.com/panuwizzle/clean-code-php)
* :fr: **French:** [errorname/clean-code-php](https://github.com/errorname/clean-code-php)
* :vietnam: **Vietnamese:** [viethuongdev/clean-code-php](https://github.com/viethuongdev/clean-code-php)
* :kr: **Korean:** [yujineeee/clean-code-php](https://github.com/yujineeee/clean-code-php)
* :tr: **Turkish:** [anilozmen/clean-code-php](https://github.com/anilozmen/clean-code-php)
* :iran: **Persian:** [amirshnll/clean-code-php](https://github.com/amirshnll/clean-code-php)
* :bangladesh: **Bangla:** [nayeemdev/clean-code-php](https://github.com/nayeemdev/clean-code-php)
* :egypt: **Arabic:** [ahmedalmory/clean-code-php](https://github.com/ahmedalmory/clean-code-php)
* :jp: **Japanese:** [hayato07/clean-code-php](https://github.com/hayato07/clean-code-php)
* :indonesia: **Indonesian:** [README.id.md](README.id.md)

**[⬆ balik ke atas](#daftar-isi-biar-gak-nyasar)**
