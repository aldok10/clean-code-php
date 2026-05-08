# Clean Code PHP (Bahasa Indonesia)

Secara umum, kode disebut bersih jika dapat dipahami dengan mudah oleh semua orang di dalam tim. Kode yang bersih dapat dibaca dan ditingkatkan oleh pengembang selain penulis aslinya. Dengan keterpahaman muncul keterbacaan, kemampuan untuk diubah, diperluas, dan dipelihara.

_____________________________________

## Aturan umum
1. Ikuti konvensi standar.
2. Tetap sederhana (KISS - Keep It Simple Stupid). Lebih sederhana selalu lebih baik. Kurangi kompleksitas sebanyak mungkin.
3. Aturan pramuka (Boy scout rule). Tinggalkan tempat perkemahan lebih bersih dari saat Anda menemukannya.
4. Selalu cari akar penyebab masalah.

## Aturan desain
1. Simpan data yang dapat dikonfigurasi di level tinggi.
2. Lebih pilih polimorfisme daripada if/else atau switch/case.
3. Pisahkan kode multi-threading.
4. Cegah konfigurabilitas yang berlebihan.
5. Gunakan dependency injection.
6. Ikuti Hukum Demeter (Law of Demeter). Sebuah kelas hanya boleh mengetahui dependensi langsungnya.

## Tips keterpahaman
1. Konsisten. Jika Anda melakukan sesuatu dengan cara tertentu, lakukan semua hal serupa dengan cara yang sama.
2. Gunakan variabel penjelas.
3. Enkapsulasi kondisi batas. Kondisi batas sulit untuk dilacak. Letakkan pemrosesan untuk kondisi tersebut di satu tempat.
4. Lebih pilih objek nilai (value object) khusus daripada tipe primitif.
5. Hindari dependensi logis. Jangan menulis metode yang bekerja dengan benar tergantung pada hal lain di kelas yang sama.
6. Hindari pengkondisian negatif.

## Aturan penamaan
1. Pilih nama yang deskriptif dan tidak ambigu.
2. Buat pembedaan yang bermakna.
3. Gunakan nama yang dapat diucapkan.
4. Gunakan nama yang dapat dicari.
5. Ganti angka ajaib (magic numbers) dengan konstanta bernama.
6. Hindari pengkodean (encodings). Jangan tambahkan awalan atau informasi tipe.

## Aturan fungsi
1. Kecil.
2. Lakukan satu hal.
3. Gunakan nama yang deskriptif.
4. Lebih pilih argumen yang lebih sedikit.
5. Tidak memiliki efek samping.
6. Jangan gunakan argumen bendera (flag). Bagi metode menjadi beberapa metode independen yang dapat dipanggil dari klien tanpa bendera tersebut.

## Aturan komentar
1. Selalu coba jelaskan diri Anda dalam kode.
2. Jangan berlebihan (redundant).
3. Jangan tambahkan kebisingan yang jelas.
4. Jangan gunakan komentar penutup kurung kurawal.
5. Jangan mengomentari kode (comment out). Hapus saja.
6. Gunakan sebagai penjelasan niat.
7. Gunakan sebagai klarifikasi kode.
8. Gunakan sebagai peringatan konsekuensi.

## Struktur kode sumber
1. Pisahkan konsep secara vertikal.
2. Kode yang terkait harus muncul padat secara vertikal.
3. Deklarasikan variabel dekat dengan penggunaannya.
4. Fungsi yang dependen harus berdekatan.
5. Fungsi yang serupa harus berdekatan.
6. Letakkan fungsi ke arah bawah.
7. Jaga baris tetap pendek.
8. Jangan gunakan penyelarasan horizontal.
9. Gunakan spasi kosong untuk mengaitkan hal-hal yang berhubungan dan memisahkan yang tidak berhubungan kuat.
10. Jangan merusak indentasi.

## Objek dan struktur data
1. Sembunyikan struktur internal.
2. Lebih pilih struktur data.
3. Hindari struktur hibrida (setengah objek dan setengah data).
4. Harus kecil.
5. Lakukan satu hal.
6. Jumlah variabel instansi yang sedikit.
7. Kelas dasar tidak boleh tahu apa-apa tentang turunannya.
8. Lebih baik memiliki banyak fungsi daripada memasukkan beberapa kode ke dalam fungsi untuk memilih perilaku.
9. Lebih pilih metode non-statis daripada metode statis.

## Pengujian
1. Satu assert per pengujian.
2. Mudah dibaca.
3. Cepat.
4. Independen.
5. Dapat diulang (repeatable).

## Bau kode (Code smells)
1. Kaku (Rigidity). Perangkat lunak sulit diubah. Perubahan kecil menyebabkan serangkaian perubahan berikutnya.
2. Rapuh (Fragility). Perangkat lunak rusak di banyak tempat karena satu perubahan.
3. Tidak bisa dipindah (Immobility). Anda tidak dapat menggunakan kembali bagian kode di proyek lain karena risiko yang terlibat dan upaya yang tinggi.
4. Kompleksitas yang tidak perlu.
5. Pengulangan yang tidak perlu.
6. Kabur (Opacity). Kode sulit dipahami.
