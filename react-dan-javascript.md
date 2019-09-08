# React Dan Javascript
Bab ini adalah bridging atau bab yang akan menjembatani teman-teman untuk belajar React JS. Sayangnya untuk mempraktikannya, harus melakukan installasi node js dan create-react-app terlebih dahulu. Tapi untuk sekedar mengerti sekilas tentang react. Boleh melanjutkan membaca.

## Sekilas Tentang React
React adalah library javascript yang berfungsi untuk membuat user interfaces. React ditulis dengan bahasa javascript dan JSX. JSX sendiri adalah templating language yang ada di javascript atau untuk lebih mudahnya bisa disebut *HTML in JS*.

## Component Based
React datang dengan memperkenalkan konsep *Component Based* yang memungkinkan developer untuk memecah semua bagian halaman web menjadi komponen - kompnen kecil. Tujuannya adalah agar komponen tersebut bisa digunakan berulang kali ataupun di halaman lain dan mudah untuk diperbaikki.

![component Based Example](./images/component-based.png)

Gambar diatas adalah contoh cara berpikir saat menggunakan React. yaitu dengan melakukan *breakdown* pada halaman hingga menjadi komponen-komponen kecil yang memiliki fungsi tertentu pada masing-masing komponennya. 

### Reusable
Semisal ada komponen `<Datepicker />` untuk mengambil inputan tanggal, dan  ingin menggunakannya di beberapa halaman. Sebelum ada React, maka harus melakukan inisiasi dengan memanggil function `$.datepicker({})` berulang kali di tiap halamannya. Berbeda saat menggunakan React, cukup meletakkan komponen `<Datepicker />` dimanapun yang diinginkan, berapapun jumlahnya tanpa harus melakukan inisiasi berulang kali.

### Easy To Mantain
Kelebihan lain dari konsep komponen based ini adalah lebih mudah untuk diperbaikki. Andai suatu saat `<Datepicker />` tak berfungsi dengan benar atau *nge-bug* atau error. Maka hanya perlu memperbaiki 1 file saja, yaitu file komponen Datepicker tersebut. Tanpa perlu mengubah semua kode di halaman tempat terpasangnya datepicker.

### Fokus Pada Fungsi
Dengan adanya komponen yang berukuran kecil-kecil, maka komponen bisa fokus pada fungsinya masing-masing. Semisal komponen `<Datepicker />` maka komponen ini hanya fokus untuk menyediakan inputan tanggal saja. Tanpa perlu tau hasil inputannya bakal diolah seperti apa nantinya, bakal dikirim kemana, dll. yang jelas dia hanya fokus untuk menyediakan inputan tanggal saja.

Dengan konsep ini, komponen hanya memegang satu fungsi fokus. Sehingga apabila ada sesuatu yang aneh atau error, bisa tau atau mengira-ngira komponen yang mana yang harus diperbaiki / dicek.


## React Itu Javascript
React sebenarnya hanyalah javascript biasa. Hanya saja React memiliki JSX yang memungkinkan untuk menulis syntax yang mirip dengan HTML kedalam file javascript. Berikut contoh komponen React dan JSX.

```jsx
import React from 'react'

const MenuAtas = () => {
  return (
    <div>
      <a href="https://website.com/">LOGO</a>
      <button>
        <i className="fa fa-bars"></i>
      </button>
    </div>
  )
}
```

Sekilas mirip HTML, tapi JSX ditulis pada file javascript. Dan nantinya JSX ini akan dirender sebagai element pada laman web.


## Functional
React erat dengan `function`. Jadi sebelum belajar React, harus paham terlebih dahulu basic dari javascript dengan mengethaui cara menggunakan function, variable, method pada variable, pemanggilan variable dll. Untuk lebih detailnya akan dibahas pada [Section Javascript](hello.md). Berikut contoh bagaimana React sangat erat dengan `function` (Functional)

```jsx
import React from 'react'
import ReactDOM from 'react-dom'

// Function biasa
const showName = () => {
  return "me"
}

console.log(showName()) // log: "me"

const ShowMe = () => {
  return (
    <div>me</div>
  )
}

ReactDOM.render(
  <ShowMe />, 
  document.querySelector('#app')
)

/*
  <div>me</div>
*/
// Saat di render maka yang muncul adalah tulisan "me" yang dibungkus oleh elemen div
```

Jadi sebenarnya component react itu hanyalah sebuah function. dan komponen jenis ini disebut **Functional Component** 


## Props
Props pada React adalah argumen yang diturunkan menuju funcitonal component. Jika teman-teman telah membaca bab function, maka perbandingannya akan menjadi seperti ini.

```javascript
import React from 'react'
import ReactDOM from 'react-dom'

// Function biasa
const greeting = (nama) => {
  return "hai:" + nama
}

console.log(greeting("Naufal")) // log: "hai: Naufal"

// Terima Props
const Greeting = (props) => {
  return (
    <div>hai: {props.nama}</div>
  )
}

ReactDOM.render(
  // Passing props
  <Greeting nama={"Naufal"} />, 
  document.querySelector('#app')
)

/*
  <div>hai: Naufal</div>
*/
```

## State
React mengenalkan konsep state. Jika props didapat dari luar, maka state diolah di dalam. Dan tidak bisa didapatkan dari luar. Karena state sifatnya terisolasi.


```javascript
import React from 'react'

class Counter extends React.Component {
  constructor() {
    this.state = {
      count: 0
    }
  }

  tambah() {
    // Untuk mengubah state pada React, cukup memanggil setState
    // Yaitu method turunan dari Class React.Component
    this.setState({ 
      count: this.state.count++ 
    })
  }

  render() {
    return (
      <div>{this.state.count}</div>
      <button onClick={this.tambah}>Tambah</button>
    )
  }
}
```

Jika diperhatikan, maka React Component diatas adalah `class` javascript biasa yang diturunkan dari `class React.Component`. Dan `state` adalah property yang ada pada class `Counter`.


## Penutup

Sekian. Terima kasih karena telah meluangkan waktunya untuk membaca mini ebook ini. Semoga bisa bermanfaat dan menjadi modal awal untuk belajar React / Vue / Angular ataupun Node JS. 



## Credits

Ebook ini dibuat oleh **Muhammad Naufal Rabbani**. Sangat mengharapkan  pertanyaan, kritik dan saran. Silahkan drop email di [bosnaufalemail@gmail.com](mailto:bosnaufalemail@gmail.com) atau hubungi langsung di telegram [@BosNaufal](https://t.me/BosNaufal) atau [facebook](https://facebook.com/BosNaufalAccount)

Semoga bisa bermanfaat dan menjadi modal awal untuk belajar React / Vue / Angular ataupun Node JS. Jangan segan untuk membagikan ebook ini....

Jadikan resource ini bermanfaat tanpa melanggar hak cipta. Ebook ini berlisensi [Attribution-NonCommercial 3.0 Unported (CC BY-NC 3.0)](https://creativecommons.org/licenses/by-nc/3.0/)

