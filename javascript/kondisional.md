# Kondisional

Merupakan salah satu komponen utama dari alogritma ataupun logika yang hendak ditulis pada suatu program. Adapun beberapa sintaks kondisional yang ada pada Javascript, yaitu: `if`, `else`, `else if`, `switch`.


## if dan else
Sekilas bila dibaca, pasti sudah bisa memahami fungsinya untuk apa. Karena sintaks ini diambil dari diksi bahasa inggris. 

Secara umum, sintaks kondisional `if` `else` javascript memiliki format sebagai berikut:

```javascript
// syarat boleh mengandung operator logika / operator perbandingan
if (syarat) {
  // scope kondisi benar / true
} else {
  // scope kondisi salah / false
}
```

Dan berikut contoh penerapannya.

```javascript
const nilai = 90
const KKM = 75
const diatasKKM = nilai >= 75
let pesan = ""

if (diatasKKM) {
  pesan = "Selamat anda lulus!"
} else {
  pesan = "Belajar yang giat yaa, besok remidi!"
}

console.log(pesan) // log: Selamat anda lulus!
```

Scope `if` akan dijalankan saat nilai syaratnya adalah `true`. Jika dilihat dari contoh diatas, nilai syaratnya diambil dari variable `diatasKKM` yang dimana bernilai `true`. Itu mengapa tulisan yang muncul pada console adalah `Selamat anda lulus!`. Sedangkan scope `else` akan dijalankan jika nilai syaratnya bernilai `false`. 

## else if
Lantas bagaimana dengan `else if`? Kalau menggunakan `if` `else` saja, itu artinya hanya memiliki 2 scope kondisi. Terkadang dibutuhkan 3 atau lebih scope kondisi yang dimana bisa dilakukan dengan menggunakan `else if`.

```javascript
const nilai = 78
let nilaiHuruf = ""

if (nilai >= 90) {
  nilaiHuruf = "A+"
} else if (nilai >= 85) {
  nilaiHuruf = "A"
} else if (nilai >= 80) {
  nilaiHuruf = "B+"
} else if (nilai >= 75) {
  nilaiHuruf = "B"
} else if (nilai >= 70) {
  nilaiHuruf = "C"
} else {
  nilaiHuruf = "D"
}

console.log(nilaiHuruf) // log: B
```

Dengan menggunakan `else if` memungkinkan untuk membuat lebih dari 2 scope kondisi. Jika dilihat dari contoh snippet diatas, disitu terdapat 5 scope kondisi yang memiliki syaratnya masing-masing.


## switch
Hampir sama dengan `else if`, `switch` memungkinkan untuk membuat beberapa scope kondisi, tapi yang jadi nilai acuan hanya 1 variabel saja. Biasanya syarat pada switch tidak diikuti dengan operator logika maupun operator perbandingan.


Umumnya, sintaks switch javascript ditulis dengan format sebagai berikut:

```javascript
// syarat TIDAK mengandung operator logika / operator perbandingan
switch (acuan) {
  case syarat1:
    // Scope jika syarat 1 terpenuhi
    break; // wajib di break;

  case syarat2:
    // Scope jika syarat 2 terpenuhi
    break;

  case syarat3:
    // Scope jika syarat 3 terpenuhi
    break;

  default:
    // Scope jika syarat 1, 2 dan 3 TIDAK terpenuhi
    break;
}
```

Berikut adalah contoh penggunaan `switch`

```javascript
const userRole = "editor"
let pesan = ""

switch (userRole) {
  case "admin":
    pesan = "Kamu adalah admin, dan bisa menuju dashboard admin"
    break;

  case "editor":
    pesan = "Kamu adalah editor, kamu hanya bisa mengakses halaman post saja"
    break;

  case "reviewer":
    pesan = "Kamu adalah reviewer, tugasmu adalah mereview artikel dari editor"
    break;

  default:
    pesan = "Kamu hanya user biasa, belajar yang giat biar bisa naik pangkat"
    break;
}

console.log(pesan) // log: Kamu adalah editor, kamu hanya bisa mengakses halaman post saja
```

`switch` ini bakal banyak digunakan di kehidupan nyata. Terutama saat menggunakan library JS yaitu redux (jika teman-teman berminat bermain React JS)