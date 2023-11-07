Tugas 7


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
![Uploading Screen Shot 2023-11-07 at 21.46.17.png…]()

