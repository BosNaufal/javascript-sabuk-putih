# Function

Adalah sebuah sebuah aksi yang dienkapsulasi agar bisa digunakan berulangkali. Tujuan menuliskan sebuah function adalah untuk menyembunyikan detail algoritma yang panjang dan rumit supaya lebih mudah digunakan. Penulisan function diawali dengan keyword `function`. 


## Penamaan
Ada beberapa jenis function dalam Javascript. Yaitu function yang bernama dan function yang tak bernama (anonymous).

> Function bernama

```javascript
// Function yang bernama greeting
function greeting() {
  console.log("Halo")
}
greeting() // log: "Halo"
```


> Anonymous Function yang dimasukkan ke dalam sebuah variable

```javascript
// Anonymous Function yang dimasukkan ke dalam sebuah variable sapa
const sapa = function() {
  console.log("Hai")
}
sapa() // log: "Hai"
```


> Anonymous Function yang dimasukkan ke dalam field sebuah object

```javascript
// Anonymous Function yang dimasukkan ke field greeting
const obj = {
  greeting() {
    console.log("Hola")
  }
}

obj.greeting() // log: "Hola"
```

## Argumen
Setiap function juga bisa menerima argumen. Boleh satu boleh lebih. berikut contoh penerimaan 1 argumen pada function 

```javascript
function greeting(nama) {
  console.log("Halo " + nama)
}

const sapa = function(orang) {
  console.log("Hai " + orang)
}

const obj = {
  greeting(user) {
    console.log("Hola " + user)
  }
}

const targetOrang =  "Naufal"

greeting(targetOrang) // log: "Halo Naufal"
sapa(targetOrang) // log: "Hai Naufal"
obj.greeting(targetOrang) // log: "Hola Naufal"
```


> Function dengan lebih dari 1 argumen

```javascript
// Contoh lebih dari satu argumen
function tambahkan(a, b) {
  const total = a + b
  console.log(total)
}

tambahkan(10, 5) // log: 15
```


## Return
`return` adalah salah satu keyword yang wajib dipahami. fungsinya adalah untuk memberikan nilai balikan pada suatu function. Berikut demonstrasinya.

```javascript
// function tak bernilai
function greeting(nama) {
  const gabungan = "Hai " + nama
}

const hasilGreeting = greeting("Naufal")
console.log(hasilGreeting) // log: undefined
```

```javascript
function sapa(nama) {
  const sapaan = "Hai " + nama
  return sapaan
}

const hasilSapa = sapa("Naufal")
console.log(hasilSapa) // log: "Hai Naufal"
```

```javascript
function tambahkan(angka1, angka2) {
  const total = angka1 + angka2
  return total
}

const hasilPertambahan = tambahkan(10, 5)
console.log(hasilPertambahan) // log: 15

// Atau bisa langsung diconsole
console.log(tambahkan(2, 5)) // log: 7
```

Nilai balikan suatu `function` tidak memiliki batasan. Jadi bisa `return` string, number, object ataupun array. Apapun itu. Contoh `return` suatu object.

```javascript
const returnObject = () => {
  return {
    nama: "Naufal",
    username: "BosNaufal"
  }
}

console.log(returnObject()) // log: { nama: "Naufal", username: "BosNaufal" }
```

