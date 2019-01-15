# ES6

Pada section ini akan dibahas beberapa bagian kecil fitur dari ES6. ES6 adalah javascript next level yang memiliki sintaks yang lebih cantik dan beberapa fitur unggulan lainnya. Ada beberapa fitur ES6 yang baiknya dikuasai terlebih dahulu untuk modal melanjutkan untuk belajar React / Vue / Angular. Tujuannya agar tulisan code lebih rapi.

## Destructure
Destructure adalah fitur ES6 yang memungkinkan untuk membongkar field suatu object atau member dari array agara menjadi variable independen.

Pada javascript model lama, harus melakukannya secara manual untuk menghasilkan nama variable yang lebih singkat untuk dipanggil.

```javascript
const user = {
  nama: "Naufal",
  usia: 21,
  alamat: "Sidoarjo",
}

const nama = user.nama
const usia = user.usia

console.log(nama, usia) // log: "Naufal", 21
```

```javascript
const dariArray = ["Naufal", "Sidoarjo"]

// Cara Manual
const nama = dariArray[0]
const alamat = dariArray[1]
```

Nah berbeda dengan ES6. Cukup melakukan ini

```javascript
const user = {
  nama: "Naufal",
  usia: 21,
  alamat: "Sidoarjo",
}

// Cara ES6
const { nama, usia } = user
console.log(nama, usia) // log: "Naufal", 21
```

```javascript
const dariArray = ["Naufal", "Sidoarjo"]

// Cara ES6
const [ nama, alamat ] = dariArray
console.log(nama, alamat) // log: "Naufal", "Sidoarjo"
```

Destructure ini sering digunakan untuk membongkar argumen object pada suatu function.

> Cara lama / manual

```javascript
const cekMobil = (mobilYangDicek) => {
  let merk = mobilYangDicek.merk
  let warna = mobilYangDicek.warna

  console.log("Mobil bermerk:", merk)
  console.log("Mobil berwarna:", warna)
}

const mobil = {
  merk: "Honda",
  warna: "Merah",
}

cekMobil(mobil)
```

> Cara ES6 (Destructure)

```javascript
const cekMobil = ({ merk, warna }) => {
  console.log("Mobil bermerk:", merk)
  console.log("Mobil berwarna:", warna)
}

const mobil = {
  merk: "Honda",
  warna: "Merah",
}

cekMobil(mobil)
```

## Spread Syntax
adalah kemampuan untuk memecah array atau object untuk diedit atau ditambah isinya. setiap spread syntax akan mengopy nilai dari array atau object tersebut secara mendetil.

```javascript
const arr = [1,2,3]
const arrBaru = [...arr, 4]
const arrLain = [0, ...arr]

console.log(arr) // log: 1,2,3
console.log(arrBaru) // log: 1,2,3,4
console.log(arrLain) // log: 0,1,2,3
```

```javascript
const obj = {
  nama: "Naufal",
  alamat: "Sidoarjo",
}

const objBaru = {
  ...obj,
  usia: 21,
}
console.log(obj) // log: { nama: "Naufal", alamat: "Sidoarjo" }
console.log(objBaru) // log: { nama: "Naufal", alamat: "Sidoarjo", usia: 21 }
```

```javascript
const argumentToPass = ["Naufal", "Sidoarjo"]

const showUser = (nama, alamat) => {
  console.log(nama, alamat)
}

showUser(...argumentToPass) // log: "Naufal", "Sidoarjo"
```


## Arrow Function
Arrow function adalah function yang tidak mempunyai context `this`. context `this` yang ada pada arrow function tergantung pada context `this` yang berada paling dekat di atasnya.

```javascript

function mobil() {
  this.merk = "Honda"

  console.log(this.merk) // log: "Honda"

  // Function biasa
  const nestedFunction = function() {
    console.log(this.merk) // log: undefined
  }

  // Arrow Function
  const arrowFunction = () => {
    console.log(this.merk) // log: "Honda"
  }

  nestedFunction()  
  arrowFunction()  
}

mobil()
```
