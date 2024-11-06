# Pro Shop Mobile
<h3> Fadhli Raihan Ardiansyah
2306207594
</h3>

<details>
<summary>
Tugas 7: Elemen Dasar Flutter

##  Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.


Stateless widget akan menampilkan data yang tidak berubah selama aplikasi berjalan, sedangkan Stateful widget bisa berubah-ubah selama aplikasi berjalan.

Perbedaan utama dari Stateless dan Stateful Widget adalah perubahan datanya. Stateless Widget memiliki data atau tampilan yang tetap, sedangkan Stateful Widget memiliki data atau tampilan yang bisa berubah.

##  Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.

#### MyApp (StatelessWidget)

MyApp adalah widget utama yang berfungsi sebagai titik masuk aplikasi. Sebagai widget stateless, MyApp tidak memiliki perubahan data yang dinamis. Aplikasi dimulai dengan MaterialApp, komponen utama Flutter untuk aplikasi berbasis material design.

#### MaterialApp 
MaterialApp adalah konfigurasi utama aplikasi yang mengatur pengaturan global, seperti title, theme, dan home

#### ThemeData 
Tema aplikasi diatur menggunakan ThemeData, khususnya pengaturan ColorScheme:

primary: Warna utama

secondary: Warna sekunder

#### MyHomePage (StatelessWidget)
MyHomePage adalah halaman utama aplikasi yang menampilkan informasi dasar seperti NPM, nama, dan kelas. Halaman ini juga memiliki daftar item menu yang diatur menggunakan widget ItemHomepage.

#### Scaffold 
Struktur dasar halaman yang menyediakan kerangka aplikasi

#### Padding 
Menambahkan jarak di sekitar widget untuk menjaga tampilan yang rapi dan mudah dibaca.

#### InfoCard (StatelessWidget) 
Sebuah kartu yang menampilkan informasi seperti judul (contoh: NPM) dan isi (misalnya nomor NPM). Menggunakan Card untuk memberikan tampilan dengan bayangan ringan.

#### SizedBox 
Menambahkan jarak antara widget atau mengatur ukuran tertentu pada widget.

#### GridView.count 
Menyusun menu aplikasi dalam bentuk grid dengan jumlah kolom tetap, yaitu tiga. Setiap item dalam grid adalah ItemCard yang berasal dari daftar ItemHomepage.

#### ItemHomepage (Model Data) 
Model data sederhana yang menyimpan nama dan ikon untuk setiap item dalam menu.

#### ItemCard (StatelessWidget) 
Sebuah kartu yang menampilkan ikon dan nama item. Dengan Material dan InkWell yang memberikan efek klik, sehingga saat item ditekan, SnackBar akan muncul.

#### SnackBar
Komponen untuk memberikan pesan sementara di bagian bawah layar saat pengguna menekan ItemCard, memberikan umpan balik langsung kepada pengguna.

##  Apa fungsi dari `setState()`? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.
Fungsi `setState()` di Flutter digunakan dalam StatefulWidget untuk memberi tahu framework bahwa ada perubahan pada state yang memerlukan pembaruan tampilan. Saat `setState()` dipanggil, Flutter akan rebuild (menggambar ulang) widget yang terkait dengan state tersebut, sehingga UI bisa merefleksikan perubahan terbaru.

Contoh variabel yang terdampak : 
Variabel counter, input teks, status tombol

##  Jelaskan perbedaan antara `const` dengan `final`.
`const` : Nilai diinisialisasi pada saat compile. Nilai tidak akan pernah berubah dan konstan selama eksekusi program
`final` : Nilai diinisialisasi pada saat runtime. Nilai tetap bisa ditentukan pada saat eksekusi program

##  Jelaskan bagaimana cara kamu mengimplementasikan checklist-checklist di atas.
### Membuat program flutter baru
Jalankan command di terminal untuk membuat proyek flutter baru
```
flutter create pro_shop
cd pro_shop
```

Rapihkan struktur proyek dengan cara membuat `menu.dart` pada direktori yang sama dengan `main.dart` kemudian pindahkan class `MyHomePage` dan `_MyHomeState` dari `main.dart` ke `menu.dart` kemudian import package yang diperlukan

### Membuat tiga tombol sederhana
Pada `menu.dart` tambahkan class `ItemHomePage` dengan atribut `name`, `icon`, dan `color`

Buat list `ItemHomePage` yang berisi tiga tombol di class `MyHomePage`

###  Mengimplementasikan warna-warna yang berbeda untuk setiap tombol (Lihat Daftar Produk, Tambah Produk, dan Logout).

Pada list `ItemHomePage` tentukan tiga warna yang berbeda untuk masing masing tombol.

Pada class `ItemCard` pastikan pada widget `build` terdapat `color : item.color`

### Memunculkan snackbar
Tambahkan kode untuk class `ItemCard`
```dart
class ItemCard extends StatelessWidget {

  final ItemHomepage item; 
  
  const ItemCard(this.item, {super.key}); 

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      borderRadius: BorderRadius.circular(12),
      
      child: InkWell(
        onTap: () {
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("Kamu telah menekan tombol ${item.name}!"))
            );
        },
        child: Container(
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```
</summary>
</details>