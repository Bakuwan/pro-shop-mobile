# Pro Shop Mobile
<h3> Fadhli Raihan Ardiansyah
2306207594
</h3>

<details>
<summary>
Tugas 7: Elemen Dasar Flutter
</summary>

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
</details>

<details>
<summary>
Tugas 8: Flutter Navigation, Layouts, Forms, and Input Elements
</summary>

## Apa kegunaan const di Flutter? Jelaskan apa keuntungan ketika menggunakan const pada kode Flutter. Kapan sebaiknya kita menggunakan const, dan kapan sebaiknya tidak digunakan?

Const digunakan untuk membuat nilai yang bersifat immutable sepanjang aplikasi dijalankan. Saat const diterapkan pada widget atau objek, Flutter akan membuatnya hanya sekali di memori sehingga menghemat penggunaan memori dan performa yang lebih baik

Gunakan const pada: nilai-nilai tetap dan widget stateless

Jangan gunakan const pada: nilai dinamis dan widget stateful

## Jelaskan dan bandingkan penggunaan Column dan Row pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!

Column menyusun widget anaknya secara vertikal sedangkan Row menyusun widget anaknya secara horizontal

Contoh implementasi Column:
```dart
Column(
  mainAxisAlignment: MainAxisAlignment.center,
  crossAxisAlignment: CrossAxisAlignment.start,
  children: <Widget>[
    Text('Text 1'),
    Text('Text 2'),
    Text('Text 3'),
  ],
)
```

Contoh implementasi Row:
```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceAround,
  crossAxisAlignment: CrossAxisAlignment.center,
  children: <Widget>[
    Icon(Icons.star),
    Text('Star'),
    Icon(Icons.favorite),
  ],
)
```

##  Sebutkan apa saja elemen input yang kamu gunakan pada halaman form yang kamu buat pada tugas kali ini. Apakah terdapat elemen input Flutter lain yang tidak kamu gunakan pada tugas ini? Jelaskan!

Elemen yang digunakan:
- TextFormField, digunakan untuk input name, amount, description, dan price
- ElevatedButton, digunakan pada tombol Save

Elemen yang tidak digunakan:
- Checkbox
- Radio
- DropdownButton
- Switch
- Slider
- DatePicker
- TimePicker
- FilePicker
- dan lain lain yang tidak diperlukan

## Bagaimana cara kamu mengatur tema (theme) dalam aplikasi Flutter agar aplikasi yang dibuat konsisten? Apakah kamu mengimplementasikan tema pada aplikasi yang kamu buat?
Pengimplementasian tema dilakukan pada komponen AppBar, Drawer, dan Button yang menggunakan colorScheme.primary

##  Bagaimana cara kamu menangani navigasi dalam aplikasi dengan banyak halaman pada Flutter?
Saya menggunakan `navigator.push` di `ItemCard`. Ketika `Tambah Produk` dipilih, halaman `ProductEntryFormPage` akan dibuka di atas halaman `MyHomePage`. Cara ini dapat diimplementasikan juga jika aplikasi memiliki halaman lain.
</details>

<details>
<summary> Tugas 9:  Integrasi Layanan Web Django dengan Aplikasi Flutter </summary>

## Jelaskan mengapa kita perlu membuat model untuk melakukan pengambilan ataupun pengiriman data JSON? Apakah akan terjadi error jika kita tidak membuat model terlebih dahulu?

Kita perlu membuat model untuk membantu dan memastikan agar data yang diambil/dikirim memiliki struktur konsisten. Dengan model kita bisa mendefinisikan tipe data yang diharapkan.

Aplikasi tidak akan langsung error jika kita tidak membuat model dan langsung memproses JSON tanpa model. Tetapi, hal ini rawan kesalahan terutama jika struktur data JSON kompleks atau data tidak konsisten.

## Jelaskan fungsi dari library http yang sudah kamu implementasikan pada tugas ini
Fungsi library HTTP adalah untuk menangani HTTP requests. Pada tugas ini, library HTTP digunakan untuk berkomunikasi antara aplikasi Flutter dan backend Django melalui API.

## Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
CookieRequest berfungsi untuk menyimpan dan mengelola cookie dengan setiap permintaan HTTP ke backend.

Instance CookieRequest dibagikan ke semua komponen aplikasi sesi pengguna konsisten dan mempermudah pengelolaan Login/Logout

##  Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.

1. Pengguna mengisi form untuk input data
2. Data dikirim ke backend menggunakan HTTP Request
3. Backend menerima dan memproses data
4. Backend mengirimkan respons
5. Flutter menangkap respons backend
6. Flutter meminta data untuk ditampilkan
7. Data ditampilkan di UI Flutter

## Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.

### Login
1. Pengguna memasukkan username dan password di form login
2. Backend Django memproses permintaan
3. Django mengembalikan respons yang menunjukkan apakah login berhasil atau gagal
4. Jika login berhasil, Flutter menavigasi pengguna ke halaman utama

### Register
1. Pengguna memasukkan username, password, dan konfirmasi password di form register
2. Backend Django akan memproses permintaan
3. Django mengembalikan respons yang menunjukkan apakah register berhasil atau gagal
4. Jika register berhasil, pengguna dinavigasi ke halaman login

### Logout
1. Flutter mengirimkan permintaan logout ke backend
2. Django memproses permintaan logout
3. Backend mengembalikan respons JSON yang menunjukkan logout berhasil
4. Setelah logout sukses Flutter menghapus cookie sesi dan menavigasi pengguna ke halaman login

## Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).

### Mengintegrasikan sistem autentikasi Django dengan proyek tugas Flutter.

1. Membuat app baru di proyek Django dengan nama `authentication`
2. Install library `django-cors-header` dan tambahkan line yang diperlukan di `settings.py`

3. Pada proyek flutter install package berikut:
```
flutter pub add provider
flutter pub add pbp_django_auth
```
4. Modifikasi root widget untuk menyediakan `CookieRequest` library ke semua child widget
### Membuat halaman login pada proyek tugas Flutter.
1. Pada file `authentication/views.py` buatlah sebuah metode view untuk login dan tambahkan routing url nya
2. Buat file baru di folder `screens` bernama `login.dart`sebagai form untuk login pengguna
3. Pada file `main.dart` ubah `home : MyPage()` menjadi `home: const LoginPage()` agar pengguna diarahkan ke halaman login

### Mengimplementasikan fitur registrasi akun pada proyek tugas Flutter.
1. Pada file `authentication/views.py` buatlah sebuah metode view untuk register dan tambahkan routing url nya
2. Buat file baru di folder `screens` bernama `register.dart`sebagai form untuk pengguna register

###  Membuat model kustom sesuai dengan proyek aplikasi Django.
1. Buka endpoint JSON di web Django yang sebelumnya sudah dibuat.
2. gunakan website `QuickType` untuk membuat model berdasarkan kode JSON yang sudah disalin
3. Buat folder `models` didalam folder `lib` dan letakkan kode model di file baru bernama `product_entry.dart`

### Membuat halaman yang berisi daftar semua item yang terdapat pada endpoint JSON di Django yang telah kamu deploy.
1. Tambahkan package HTTP ke flutter
2. Tambahkan kode berikut ke `AndroidManifest.xml` agar aplikasi flutter bisa mengakses internet
```xml
<uses-permissionandroid:name="androiINTERNET" />
```
3. Buat file baru di folder `screens` bernama `list_productentry.dart`
4. Buat kode untuk menampilkan data dari endpoint JSON di Django.

### Membuat halaman detail untuk setiap item yang terdapat pada halaman daftar Item.
1. Buat file baru di folder `screens` bernama `product_detail.dart` dan tambahkan kode untuk menampilkan detail sebuah produk.
2. Modifikasi file `list_productentry.dart`, tambahkan navigasi ke `ProductDetailPage` saat produk ditekan.

### Melakukan filter pada halaman daftar item dengan hanya menampilkan item yang terasosiasi dengan pengguna yang login.
Karena data item sudah di filter dari backend, kita tinggal mengambil data dari endpoint JSON

</details>