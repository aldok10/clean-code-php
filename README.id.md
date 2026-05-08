# Clean Code PHP (Versi Gen Z 2026)

Gini ya, kode itu dianggap 'clean' kalo vibes-nya dapet dan gampang dipahami sama semua orang di tim. Kode yang clean itu bukan cuma elu yang ngerti, tapi dev lain juga bisa baca dan upgrade tanpa kena mental. Kalo udah paham, ngerawatnya juga jadi slay, gampang diubah, dan gak bikin pusing, no cap!

_____________________________________

## Aturan Umum (General Rules)
1. Ikuti konvensi standar, jangan sok asik bikin aturan sendiri.
2. KISS (Keep It Simple Stupid). Makin simpel makin GG. Kurangi keribetan semaksimal mungkin, biar gak *cooked*.
3. Boy scout rule. Balikin tempat kemah lebih bersih dari pas lu dateng. Kalo liat kode berantakan, rapihin dikit lah.
4. Selalu cari root cause. Jangan cuma benerin permukaannya doang, cari masalah utamanya biar gak *red flag*.

## Aturan Desain (Design Rules)
1. Simpan data konfigurasi di level tinggi, jangan diumpetin di dalem-dalem.
2. Pake polimorfisme daripada if/else atau switch/case yang kepanjangan. Biar lebih *clean*.
3. Pisahin kode multi-threading biar gak *cluttered*.
4. Jangan over-configurability, secukupnya aja biar gak pusing.
5. Pake Dependency Injection. Ini kuncinya biar kode lu gak kaku.
6. Law of Demeter. Sebuah kelas cuma boleh kenal sama bestie-nya (dependensi langsung) doang.

## Tips Keterpahaman (Understandability Tips)
1. Konsisten terus. Kalo lu udah pake satu cara, ya pake cara itu terus buat hal serupa. Jangan menye-menye.
2. Pake variabel penjelas. Jangan cuma $x atau $y, gak jelas banget.
3. Enkapsulasi kondisi batas. Kondisi yang ribet taruh di satu tempat aja biar gak *chaos*.
4. Pake value objects daripada tipe primitif. Lebih berkelas gitu loh.
5. Hindari dependensi logis. Jangan bikin metode yang jalannya tergantung 'mood' hal lain di kelas yang sama.
6. Hindari pengkondisian negatif. Pake yang positif-positif aja biar gak pusing bacanya.

## Aturan Penamaan (Names Rules)
1. Pilih nama yang deskriptif dan gak ambigu. Gak usah tebak-tebakan.
2. Bikin pembedaan yang bermakna. Jangan asal beda doang.
3. Pake nama yang bisa diucapin, biar pas ngobrol gak keseleo lidah.
4. Pake nama yang gampang dicari (searchable).
5. Ganti magic numbers pake konstanta bernama. Gak jelas banget itu angka dateng dari mana.
6. Hindari encoding. Gak usah pake prefix atau info tipe yang ribet-ribet.

## Aturan Fungsi (Functions Rules)
1. Kecil aja, jangan kayak novel.
2. Satu fungsi satu tugas. Jangan serakah.
3. Pake nama yang deskriptif, biar langsung paham itu fungsi buat apa.
4. Argumen dikit aja, makin dikit makin mantap.
5. Gak boleh ada efek samping (side effects) yang aneh-aneh.
6. Jangan pake argumen bendera (flag). Mending dipisah jadi fungsi sendiri-sendiri, biar lebih *straightforward*.

## Aturan Komentar (Comments Rules)
1. Usahain kodenya udah jelas sendiri tanpa perlu dikomenin.
2. Jangan berlebihan, gak usah curhat di komen.
3. Jangan nambahin kebisingan yang gak perlu.
4. Gak usah pake komen di penutup kurung kurawal, ganggu pemandangan.
5. Jangan komenin kode lama (comment out). Hapus aja, kan ada Git, no worries!
6. Pake buat jelasin niat lu apa (intent).
7. Pake buat klarifikasi bagian yang emang agak *tricky*.
8. Pake buat kasih peringatan konsekuensi kalo kode itu diubah asal-asalan.

## Struktur Kode Sumber (Source Code Structure)
1. Pisahin konsep secara vertikal.
2. Kode yang se-vibe harus deketan secara vertikal.
3. Deklarasi variabel deket sama tempat pakenya.
4. Fungsi yang saling ketergantungan harus deketan.
5. Fungsi yang mirip juga harus deketan.
6. Taruh fungsi ke arah bawah (downward direction).
7. Baris jangan kepanjangan, capek scroll-nya.
8. Gak usah diselarasin secara horizontal (horizontal alignment), malah aneh liatnya.
9. Pake spasi buat misahin atau nyatuin hal yang emang nyambung.
10. Jangan ngerusak indentasi, *red flag* banget itu.

## Objek dan Struktur Data
1. Sembunyiin struktur internal. Rahasia perusahaan!
2. Lebih pilih struktur data yang simpel.
3. Hindari struktur hibrida (setengah objek setengah data). Gak jelas identitasnya.
4. Harus kecil, jangan kegedean.
5. Satu tugas aja cukup.
6. Variabel instansi dikit aja.
7. Kelas dasar gak boleh tau apa-apa soal turunannya.
8. Mending punya banyak fungsi daripada masukin kode buat milih perilaku.
9. Lebih pilih metode non-statis daripada statis, biar lebih fleksibel.

## Pengujian (Tests)
1. Satu assert per test. Gak usah borongan.
2. Harus gampang dibaca, biar tau kalo error kenapa.
3. Harus kenceng (fast). Gak jaman nunggu lama.
4. Independen, jangan tergantung sama test lain.
5. Bisa diulang kapan aja (repeatable) dengan hasil yang sama.

## Bau Kode (Code Smells)
1. Kaku (Rigidity). Kode susah diubah, sekali ubah dikit malah merembet ke mana-mana.
2. Rapuh (Fragility). Sekali diubah, eh malah rusak semua di tempat lain. Gak slay banget.
3. Gak bisa dipindah (Immobility). Kode susah dipake lagi di tempat lain karena terlalu kaku.
4. Kompleksitas yang gak perlu. Gak usah sok ribet.
5. Pengulangan yang gak perlu. Jangan kayak kaset rusak.
6. Kabur (Opacity). Kode susah dimengerti, bikin pusing tujuh keliling.
