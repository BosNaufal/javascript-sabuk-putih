# Import Export

`import` dan `export` adalah keyword yang digunakan untuk mengekspos sebuah module dan untuk menggunakannya di module lain. 

Jadi, jika menggunakan [Node JS](https://nodejs.org/en/) atau [Webpack](https://webpack.js.org/), maka antara file javascript yang satu dengan yang lain, tidak saling berhubungan, variabelnya tidak bisa diakes secara langsung satu sama lain. kecuali melakukan `export` dan `import`.

## Kasus

Oke semisal ada 2 file javascript. yang satu adalah kumpulan variable, yang satu adalah function yang berusaha mengakses variable-variable tersebut.


```javascript
// file: biodata.js

const biodata = {
  nama: "Naufal",
  umur: 21,
  asal: "Sidoarjo",
}

console.log(biodata) // log: { nama: "Naufal", ... }
```

```javascript
// file: main.js

console.log(biodata) // error
// Karena variable biodata tidak ada pada file ini

const getUserInfo = (info) => {
  console.log("Nama:  " + info.nama)
  console.log("Umur: " + info.umur)
  console.log("Asal: " + info.asal)
}

getUserInfo(biodata) // error
// Karena variable biodata tidak ada pada file ini
```

## Basic
Tapi jika melakukan export import, maka antar module bisa berbagi variable. Semisal

```javascript
// file: biodata.js

const biodata = {
  nama: "Naufal",
  umur: 21,
  asal: "Sidoarjo",
}

export default biodata
```

```javascript
// file: main.js

/*
  biodataUser adalah nama alias dari variable yang diimport
  nama alias bisa diganti bebas
*/
import biodataUser from './biodata.js' 

console.log(biodataUser) // log: { nama: "Naufal", ... }

const getUserInfo = (info) => {
  console.log("Nama:  " + info.nama)
  console.log("Umur: " + info.umur)
  console.log("Asal: " + info.asal)
}

getUserInfo(biodataUser)
/**
  log: 
    Nama: Naufal
    Umur: 21
    Asal: sidoarjo
**/
```

## Export Type

Ada beberapa cara untuk melakukan `export`. yaitu dengan `export` biasa, dan `export default`. 

`export default` ini akan memberikan nilai sesuai nilai variable yang diexport tanpa harus mengimportnya secara spesifik.

Sedangkan `export` biasa akan mewajibkan untuk memilih bagian module mana yang hendak di-`import` secara spesifik

```javascript
// file: biodata.js

const user = {
  nama: "Naufal",
  lastName: "Rabbani",
  umur: 21,
  asal: "Sidoarjo",
}

// Perhatikan
export {
  fullName: (user.name + user.lastName),
}

// Perhatikan
export default user
```

> import tidak sepesifik (default)

```javascript
// file: main.js
import biodataUser from './biodata.js' 
```

> import sepesifik. Wajib menuliskan nama variablenya

```javascript
// file: main.js
import { fullName } from './biodata.js' 
```

> Penggunaan import default dan import spesifik secara bersamaan.

```javascript
// file: main.js
import biodataUser, { fullName } from './biodata.js' 

console.log(biodataUser) // log: { nama: "Naufal", ... }

console.log(fullName) // log: "Naufal Rabbani"
```