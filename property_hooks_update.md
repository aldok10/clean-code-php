
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
