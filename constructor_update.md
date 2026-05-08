
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
