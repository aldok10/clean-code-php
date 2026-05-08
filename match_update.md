
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
