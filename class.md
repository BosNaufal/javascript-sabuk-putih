# Class Javascript

Javascript lebih identik dengan functional programing. Tapi bukan berarti di Javascript tidak ada OOP (Object Oriented Programming). ES6 menghadirkan sintaks baru yaitu `class` yang telah diadopsi dan digunakan dibanyak library JS. React pun menggunakan `ES6 Class`.

## Class

`class` adalah gambaran atau rancangan atau blueprint dari suatu `object instance`. Terkadang agak membingungkan di javascript karena ada `object type` ada juga `object instance`. [Object Type](tipe-data.md#object) adalah variabel bertipe object yang telah dibahas sebelumnya. sedangkan `object instance` adalah hasil dari inisiasi suatu `class`.

```javascript
class Mobil {
  constructor() {
    this.merk = "Honda"
  }

  cekMerk() {
    console.log(this.merk)
  }
}

// Inisiasi object instance
const mobilku = new Mobil();
mobilku.cekMerk() // log: "Honda"
```

Jika melihat contoh kode diatas, `Mobil` adalah nama `class` atau nama blueprint. Sedangkan `mobilku` adalah variabel yang berisi `object instance` dari `class Mobil`.

> Satu `class` bisa menghasilkan beberapa `object instance`.

```javascript
class Mobil {
  constructor(merk) {
    this.merk = merk
  }

  cekMerk() {
    console.log(this.merk)
  }
}

// Inisiasi object instance
const mobilku = new Mobil("Alphard");
mobilku.cekMerk() // log: "Alphard"

const mobilnya = new Mobil("Honda");
mobilnya.cekMerk() // log: "Honda"
```

Dari contoh diatas, terdapat 2 `object instance` dari 1 `class Mobil`. yang tidak saling mempengaruhi satu sama lain. 


## Property
Property adalah atribut yang melekat pada suatu class. Misal, ada `class Mobil` maka property yang bisa dibuat untuk `class Mobil` adalah merk, warna, jenis, dsb. 

Dan berikut contoh penulisan property pada suatu class

```javascript
class Mobil {
  constructor() {
    this.merk = "Honda"
    this.warna = "hitam"
    this.jenis = "sedan"
    this.roda = 4
  }
}
```

Untuk mengakses ataupun mengedit suatu property, menggunakan `this.namaProperty`.

```javascript
class Mobil {
  constructor() {
    this.merk = "Honda"
    this.warna = "hitam"
    this.jenis = "sedan"
    this.roda = 4
  }

  hitungRoda() {
    console.log(this.roda)
  }

  tambahRoda() {
    this.roda++
    this.hitungRoda()
  }
}

// Inisiasi object instance
const mobilku = new Mobil()
mobilku.hitungRoda() // log: 4
mobilku.tambahRoda() // log: 5
```


## Method

Method adalah sebuah aksi yang ada pada suatu `class`. Method berbentuk `function`. Method pada suatu class mempunyai *behaviour* yang sama dengan function. Ada baiknya teman-teman membaca terlebih dahulu bab tentang [function](function.md)

```javascript
class Mobil {
  constructor() {
    this.merk = "Honda"
    this.warna = "hitam"
    this.jenis = "sedan"
    this.roda = 4
  }

  getWarna() {
    console.log(this.warna)
  }

  gantiWarna(warna) {
    this.warna = warna
  }
}

// Inisiasi object instance
const mobilku = new Mobil()
mobilku.getWarna() // log: hitam
mobilku.gantiWarna("pink")
mobilku.getWarna() // log: pink
```

Dari kode diatas, `getWarna` dan `gantiWarna` adalah sebuah method dari `class Mobil`. Apakah constructor juga sebuah method?

## Constructor
`constructor` juga merupakan sebuah method yang dijalankan pertama kali saat proses inisiasi sebuah `object instance`.

```javascript
class Mobil {
  constructor() {
    console.log("ini auto jalan duluan!")
  }

  methodBiasa() {
    console.log("Aktif bila dipanggil")
  }
}

// Inisiasi object instance
const mobilku = new Mobil() // log: ini auto jalan duluan!
mobilku.methodBiasa() // log: Aktif bila dipanggil
```

## this
context `this` adalah salah satu bab yang harusnya dibahas lebih dalam. tapi untuk saat ini, teman-teman cukup perlu tahu bahwa `this` berfungsi untuk mengakses keseluruhan yang ada pada class. Entah itu sebuah `property` maupun `method`.

```javascript
class Mobil {
  constructor() {
    // untuk set property
    this.roda = 4
  }

  hitungRoda() {
    // Untuk akses property
    console.log(this.roda)
  }

  tambahRoda() {
    this.roda++
    // Untuk memanggil method dari class Mobil itu sendiri
    this.hitungRoda()
  }
}
```

> Jadi, `method` maupun `property` bisa saling memanggil satu sama lain.


## static
`static` adalah sebuah tanda bahwa suatu  `method` pada `class` tersebut bisa diakses secara langsung tanpa harus melakukan inisiasi terlebih dahulu.

```javascript
class Siswa {
  constructor() {
    this.nama = "Rinjani"
  }

  static bisaLangsung() {
    console.log("Langsung Akses!")
  }

  methodBiasa() {
    console.log("Method biasa")
  }
}

Siswa.bisaLangsung() // log: Langsung Akses!
Siswa.methodBiasa() // error: Siswa.methodBiasa is not a function
```

Hanya saja pada method `static` tidak bisa mengakses konteks `this`. Jadi tidak bisa mengakses property yang ada pada `class` tersebut.

```javascript
class Siswa {
  constructor() {
    this.nama = "Rinjani"
  }

  static bisaLangsung() {
    console.log("Langsung Akses!", this.nama)
  }

  methodBiasa() {
    console.log("Method biasa", this.nama)
  }
}

// Menggunakan inisiasi
const siswaBaik = new Siswa()
siswaBaik.methodBiasa() // log: Method biasa Rinjani

// Tanpa inisiai
Siswa.bisaLangsung() // log: Langsung Akses! undefined
```


## Inheritance
Inheritance biasa disebut turunan. Yang artinya bisa menambahkan atau memodifikasi class yang sudah ada tanpa harus menyentuhnya secara langsung. Semua behaviour yang ada pada class induk akan ikut terbawa pada class turunannya.

```javascript
class Induk {
  constructor() {
    this.nama = "Induk"
    console.log("Aku siap!")
  }

  methodInduk() {
    console.log("Namaku", this.nama)
  }
}

class Anak extends Induk {
  constructor() {
    // wajib dipanggil untuk memanggil constructor dari parent
    super()
  }

  methodTambahanDariAnak() {
    console.log("Namaku dari:", this.nama)
  }
}

const induknya = new Induk() // log: Aku siap!
induknya.methodInduk() // log: Namaku Induk

const anaknya = new Anak() // log: Aku siap!
anaknya.methodTambahanDariAnak() // log: Namaku dari: Induk
anaknya.methodInduk() // log: Namaku Induk -> method dari induk tetap ada 
```

Perhatikan contoh diatas. padahal pada kelas Anak, tidak ada property `nama` tapi `class Anak` tetap memiliki property nama yang berasal dari Induk.

Perhatikan lagi pada constructor. pada saat pertama kali inisiasi, `class Induk` akan mengatakan `aku siap!` pada class `Anak` juga begitu. karena constructor dari Induk, diturunkan ke class Anak. Itu yang menyebabkan behaviour dari keduanya sama.