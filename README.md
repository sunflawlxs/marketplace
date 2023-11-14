<details>
<summary>Tugas 7</summary>


# Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?
Stateless widget dan stateful widget adalah dua jenis widget yang tersedia di Flutter. Stateless widget adalah widget yang tidak memiliki keadaan internal, sedangkan stateful widget adalah widget yang memiliki keadaan internal. Dalam konteks pengembangan aplikasi Flutter, perbedaan utama antara keduanya adalah bahwa stateless widget digunakan ketika kita ingin menampilkan sesuatu yang statis, sedangkan stateful widget digunakan ketika kita ingin menampilkan sesuatu yang dinamis dan dapat berubah.

Stateless widget biasanya digunakan untuk menampilkan informasi yang tidak berubah, seperti teks atau gambar. Stateless widget tidak memiliki keadaan internal, sehingga tidak dapat berubah selama aplikasi berjalan. Stateless widget lebih efisien daripada stateful widget karena tidak memerlukan pengelolaan keadaan internal.

Di sisi lain, stateful widget digunakan ketika kita ingin menampilkan sesuatu yang dapat berubah selama aplikasi berjalan. Stateful widget memiliki keadaan internal, sehingga dapat berubah selama aplikasi berjalan. Stateful widget biasanya digunakan untuk menampilkan informasi yang dapat berubah, seperti input pengguna atau data dari database. Namun, karena stateful widget memerlukan pengelolaan keadaan internal, ia lebih kompleks dan kurang efisien daripada stateless widget.

# Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.
| Nama *Widget* | Fungsi |
| --- | --- |
| `MyHomePage` | *Stateless widget* untuk mengatur tampilan utama aplikasi |
| `Scaffold` | Untuk kerangka utama dari halaman, yang mencakup `AppBar` dan `Body` |
| `AppBar` | Untuk menampilkan bilah atas pada halaman, yaitu `marketplace` |
| `SingleChildScrollView` | Untuk membuat area konten yang dapat digulir jika konten melebihi ukuran layar |
| `Padding` | Untuk menambahkan jarak di sekitar *widget-child* |
| `Column` | Untuk mengatur *widget-children* secara vertikal |
| `Text` | Untuk menampilkan teks `Welcome to marketplace!` pada tengah halaman |
| `GridView.count` | Untuk membuat tata letak grid dengan jumlah kolom yang tetap |
| `ShopItem` | Kelas yang mendefinisikan item toko yang memiliki nama, ikon, dan warna |
| `ShopCard` | Untuk mewakili *card* yang menampilkan item toko |
| `Material` | Untuk mengatur bahan dasar *card* dengan warna latar belakang yang sesuai |
| `InkWell` | Untuk membuat area responsif terhadap sentuhan (*tap*) |
| `Container` | Untuk mengelola tata letak dan konten dalam *card* |
| `Icon` | Untuk menampilkan ikon dalam kartu |
| `SnackBar` | Untuk menampilkan pesan singkat yang muncul di bawah layar saat item toko diklik |
| `MyApp` | Untuk menginisialisasi dan mengkonfigurasi aplikasi |
| `MaterialApp` | Untuk mengkonfigurasi dan mengatur tema aplikasi, termasuk `title`, `theme`, dan `home` |
| `ColorScheme` | Untuk mengatur palet warna dalam aplikasi |
| `useMaterial3` | Untuk mengaktifkan penggunaan `Material You` |

<br>

*Source:*
* https://www.geeksforgeeks.org/what-is-widgets-in-flutter/



# Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step 
#### Membuat Proyek Flutter Baru
1.  membuat folder dengan nama `marketplace`. 
<br>

2.  *generate* proyek Flutter baru dengan nama `marketplace`. Lalu, masuk ke dalam direktori proyek seperti berikut.
```bash
flutter create marketplace
cd marketplace
```


3.  menjalanlan proyek melalui Command Prompt seperti berikut.
```bash
flutter run
```


4. menjalankan perintah untuk *enable web support* dan menjalankan proyek di aplikasi Google Chrome seperti berikut.
```bash
flutter config --enable-web
flutter run -d chrome
```

5. Lalu, saya melakukan `git init` pada *root folder* dan `add`, `commit`, `push` proyek ke repositori baru di GitHub dengan nama `marketplace`.
<br>

#### Merapikan Struktur Proyek
1. Pertama, saya membuat file baru bernama `menu.dart` pada direktori `marketplace/lib` dan mengimpor kode seperti berikut.
```dart
import 'package:flutter/material.dart';
```


2. Pada `main.dart`, saya memotong kode baris ke-39 sampai akhir yang berisi *class* seperti berikut. Lalu, saya pindahkan ke `menu.dart`.
```dart
class MyHomePage ... {
    ...
}

class _MyHomePageState ... {
    ...
}
```

3. Selanjutnya, saya mengimpor suatu kode untuk menghilangkan *error* pada `main.dart` seperti berikut.
```bash
import 'package:marketplace/menu.dart';
```


#### Membuat Widget Sederhana pada Flutter
1. Awalnya, saya membuka file `main.dart`. Lalu, mengubah kodenya pada bagian tema aplikasi yang mempunyai tipe `Material Color` seperti berikut.
```dart
colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
```


2. Kedua, saya menghapus `MyHomePage(title: 'Flutter Demo Home Page')` pada file `main.dart` menjadi seperti berikut.
```dart
MyHomePage()
```


3. Pada file `menu.dart`, saya mengubah sifat *widget* menjadi *stateless* dengan melakukan perubahan pada `({super.key, required this.title})` menjadi `({Key? key}) : super(key: key);` dan menghapus `final String title;` sampai bawah serta menambahkan *Widget Build* sehingga terlihat seperti berikut.
```dart
class MyHomePage extends StatelessWidget {
    MyHomePage({Key? key}) : super(key: key);

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            ...
        );
    }
}
```

4. Kemudian, saya menambahkan teks dan *card* serta memulai *define* tipe pada list yang saya punya seperti berikut.
```dart
class ShopItem {
  final String name;
  final IconData icon;
  final Color color;

  ShopItem(this.name, this.icon, this.color);
}
```

5. Lalu, pada bagian bawah kode `MyHomePage({Key? key}) : super(key: key);`, saya menambahkan nama, harga, dan ikon barang seperti berikut.
```dart
final List<ShopItem> items = [
    ShopItem("Lihat Item", Icons.checklist, Colors.pink),
    ShopItem("Tambah Item", Icons.add_shopping_cart, Colors.lightGreen),
    ShopItem("Logout", Icons.logout, Colors.blue),
  ];
```

6. Kemudian, saya menambahkan kode dalam *widget build* seperti berikut.
```dart
    return Scaffold(
      appBar: AppBar(
        title: const Text(
          'marketplace',
        ),
      ),
      body: SingleChildScrollView(
        child: Padding(
          padding: const EdgeInsets.all(10.0),
          child: Column(
            children: <Widget>[
              const Padding(
                padding: EdgeInsets.only(top: 10.0, bottom: 10.0),
                child: Text(
                  'Welcome to marketplace!', 
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),
              GridView.count(
                primary: true,
                padding: const EdgeInsets.all(20),
                crossAxisSpacing: 10,
                mainAxisSpacing: 10,
                crossAxisCount: 3,
                shrinkWrap: true,
                children: items.map((ShopItem item) {
                  return ShopCard(item);
                }).toList(),
              ),
            ],
          ),
        ),
      ),
    );
``` 


7. Dikarenakan masih terdapat *error*, saya harus membuat *widget stateless* untuk menampilkan *card* seperti berikut.
```dart
class ShopCard extends StatelessWidget {
  final ShopItem item;

  const ShopCard(this.item, {super.key});

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      child: InkWell(
        onTap: () {
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
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


8. git `add`, `commit`, `push`

## BONUS Part 1**
<img width="1280" alt="Screen Shot 2023-11-07 at 21 46 29" src="https://github.com/sunflawlxs/marketplace/assets/123561471/101be2d7-3302-4c11-a907-ca415b2b2898">
</details>

<details>
TUGAS 8
# Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!
Navigator.push() dan Navigator.pushReplacement() adalah dua metode yang digunakan untuk melakukan navigasi antara halaman dalam aplikasi Flutter. Perbedaan utama antara kedua metode ini adalah:

Navigator.push() menambahkan halaman baru ke atas tumpukan navigasi, tanpa menghapus halaman sebelumnya. Ini berarti kita bisa kembali ke halaman sebelumnya dengan menekan tombol kembali atau memanggil Navigator.pop().
Navigator.pushReplacement() menggantikan halaman saat ini dengan halaman baru, dan menghapus halaman saat ini dari tumpukan navigasi. Ini berarti kita tidak bisa kembali ke halaman sebelumnya, karena halaman tersebut sudah dihapus. Contohnya adalah pergantian halaman sederhana, seperti dari halaman 'Home' ke halaman 'Lihat Produk'. Namun, Navigator.pushReplacement() akan menampilkan halaman baru tanpa riwayat halaman sebelumnya atau tidak kembali ke halaman sebelumnya jika tombol back ditekan. Method pushReplacement() menghapus route yang sedang ditampilkan kepada pengguna dan menggantinya dengan suatu route. Method ini menyebabkan aplikasi untuk berpindah dari route yang sedang ditampilkan kepada pengguna ke suatu route yang diberikan. Route lama pada atas stack akan digantikan secara langsung oleh route baru yang diberikan tanpa mengubah kondisi elemen stack yang berada di bawahnya (perhatikan urutan stack). Contoh penggunaannya adalah halaman 'Login', setelah user berhasil login akan masuk ke halaman 'Home'. Untuk itu kita tidak menginginkan user kembali ke halaman 'Login' jika tombol back ditekan.

# Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!
- Untuk mengatur ruang/jarak/posisi/penempatan widget-child:
Container: Widget dasar untuk mengatur posisi, warna, dan ukuran layar dari beberapa widget-child
Padding: Memberikan jarak dari dalam widget menuju widget lainnya
Margin: Memberikan jarak di antara widget
Align: Menempatkan widget di posisi topLeft, topRight, bottomLeft, bottomRight, dsb.
Stack: Menempatkan widget di atas satu sama lain (bertumpuk)

- Untuk menampilkan data/item yang dapat digulir
Row: Mengatur posisi widget yang berada dalam row secara vertikal atau ke kiri
Column: Mengatur posisi widget yang berada dalam column secara horizontal atau ke bawah
ListView: Mengatur widget dalam daftar gulir vertikal atau horizontal

- Untuk menampilkan data/item dalam bentuk tabel
GridView: Mengatur widget dalam susunan dua dimensi

- Elemen Input Form yang Digunakan
Elemen-elemen input pada proyek ini menggunakan field TextFormField agar dapat dilakukan validasi dan integrasi, yaitu:
Nama Ramuan (String karena nama ramuan berupa teks)
Jumlah (int karena jumlah berupa digit angka)
Harga (int karena harga berupa digit angka)
Deskripsi (String karena deskripsi berupa teks)

# Bagaimana penerapan clean architecture pada aplikasi Flutter?
Clean architecture adalah salah satu cara untuk membuat aplikasi Flutter yang bersih, rapi, mudah dipelihara, dan dapat diuji. Clean architecture membagi aplikasi menjadi beberapa lapisan, yaitu:

- Lapisan domain, yang berisi logika bisnis dan model data aplikasi. Lapisan ini tidak bergantung pada kerangka kerja Flutter atau sumber data eksternal, sehingga dapat digunakan kembali di berbagai lingkungan.
- Lapisan aplikasi, yang berisi kasus penggunaan aplikasi dan menjembatani lapisan infrastruktur dan presentasi. Lapisan ini juga tidak bergantung pada kerangka kerja Flutter, tetapi bergantung pada lapisan domain. Lapisan ini biasanya menggunakan pola desain seperti BLoC, Provider, atau Riverpod untuk mengelola keadaan aplikasi.
- Lapisan infrastruktur, yang berisi interaksi dengan dunia luar, seperti basis data, server web, atau antarmuka pengguna. Lapisan ini bergantung pada kerangka kerja Flutter dan lapisan aplikasi. Lapisan ini biasanya menggunakan paket seperti dio, http, sqflite, atau firebase untuk mengakses sumber data eksternal.
- Lapisan presentasi, yang berisi kode yang menampilkan antarmuka pengguna, di mana permintaan dibuat dan respons dikembalikan. Lapisan ini juga bergantung pada kerangka kerja Flutter dan lapisan aplikasi. Lapisan ini biasanya menggunakan widget Flutter untuk membuat tata letak, animasi, dan gaya aplikasi.

Untuk menerapkan clean architecture pada aplikasi Flutter, kita perlu mengikuti beberapa langkah, yaitu:

- Membuat folder untuk setiap lapisan, misalnya domain, application, infrastructure, dan presentation.
- Membuat file untuk setiap entitas, kasus penggunaan, repositori, sumber data, dan halaman dalam folder yang sesuai.
- Membuat kelas abstrak untuk repositori dan sumber data di lapisan domain, yang akan diimplementasikan oleh kelas konkret di lapisan infrastruktur.
- Membuat kelas untuk BLoC, Provider, atau Riverpod di lapisan aplikasi, yang akan mengelola keadaan aplikasi dan menghubungkan lapisan domain dan presentasi.
- Membuat widget untuk halaman, komponen, dan dialog di lapisan presentasi, yang akan menampilkan antarmuka pengguna dan mengirimkan permintaan ke lapisan aplikasi.
- Menggunakan dependency injection untuk menyediakan ketergantungan kelas ke kelas lain, misalnya menggunakan paket seperti get_it, injectable, atau kiwi.

# Langkah Implementasi Checklist
Membuat shoplist_form.dart untuk halaman formulir tambah ramuan yang memiliki 4 elemen input: name, amount, price, dan description, tombol save, validasi tiap elemen, dan pop up data item setelah save form
Memindahkan class ShopItem dan ShopCard dari menu.dart ke file baru shop_card.dart
Pada shop_card.dart, mengatur Navigator.push() atau routing dari card Tambah Ramuan di halaman utama ke halaman formulir
Membuat left_drawer.dart untuk drawer yang memiliki opsi Halaman Utama yang akan routing ke halaman utama jika ditekan dan Tambah Ramuan yang akan routing ke halaman formulir jika ditekan
Membuat shop_card.dart untuk widget card yang menampilkan produk ramuan
Membuat items.dart untuk halaman daftar ramuan yang akan menampilkan card dari shop_card.dart
Menambahkan ListTile Lihat Ramuan di left_drawer.dart yang route ke halaman daftar ramuan
Menambahkan routing dari card Lihat Ramuan di halaman utama ke halaman daftar ramuan pada shop_card.dart
Membuat direktori baru screens dan widgets di direktori lib
Memindahkan items.dart, menu.dart, dan shoplist_form.dart ke direktori screens
Memindahkan items_card.dart, left_drawer.dart, dan shop_card.dart ke direktori widgets

# BONUS
sudah diimplementasi 

Referensi:
https://ngasturi.id/2020/01/04/flutter-navigasi-antar-halaman/
https://medium.com/komandro-ccit-ftui/tutorial-flutter-layout-be8cfb66904a

</details>
