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
<summary>Tugas 8</summary>
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
1. Pertama, saya mengubah kode yang ada pada `main.dart` sebagai berikut.
```dart
import 'package:flutter/material.dart';
import 'package:marketplace/screens/menu.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter PBP',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
        useMaterial3: true,
      ),
      home: MyHomePage(),
    );
  }
}
```
<br>

2. Kemudian, pada `lib`, saya membuat folder baru bernama `screens` dan `widgets` di dalamnya. Selain itu, saya memindahkan `menu.dart` ke dalam folder `screens`
<br>

3. Lalu, saya menambah dan mengubah beberapa kode pada `menu.dart` seperti berikut.
```dart
import 'package:flutter/material.dart';
import 'package:marketplace/widgets/left_drawer.dart';
import 'package:marketplace/widgets/menu_card.dart';

class MyHomePage extends StatelessWidget {
  MyHomePage({Key? key}) : super(key: key);

  final List<ShopItem> items = [
    ShopItem("Show Items", Icons.checklist, Colors.pink),
    ShopItem("Add an Item", Icons.add_shopping_cart, Colors.lightGreen),
    ShopItem("Logout", Icons.logout, Colors.blue),
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text(
          'marketplace',
        ),
        backgroundColor: Colors.indigo,
        foregroundColor: Colors.white,
      ),
      drawer: const LeftDrawer(),
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
  }
}
```
<br>

4. Selanjutnya, saya membuat `left_drawer.dart` pada direktori `lib/widgets/` sebagai berikut.
```dart
import 'package:flutter/material.dart';
import 'package:marketplace/screens/menu.dart';
import 'package:marketplace/screens/marketplace_form.dart';
import 'package:marketplace/screens/marketplace_show.dart';

class LeftDrawer extends StatelessWidget {
  const LeftDrawer({super.key});

  @override
  Widget build(BuildContext context) {
    return Drawer(
      child: ListView(
        children: [
          const DrawerHeader(
            decoration: BoxDecoration(
              color: Colors.indigo,
            ),
            child: Column(
              children: [
                Text(
                  'marketplace',
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                    color: Colors.white,
                  ),
                ),
                Padding(padding: EdgeInsets.all(10)),
                Text(
                  "Simplified inventory management and time-saving efficiency!",
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 15,
                    color: Colors.white,
                    fontWeight: FontWeight.normal,
                  ),
                ),
              ],
            ),
          ),
          ListTile(
            leading: const Icon(Icons.home_outlined),
            title: const Text('Main Page'),
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => MyHomePage(),
                  ));
            },
          ),
          ListTile(
            leading: const Icon(Icons.add_shopping_cart),
            title: const Text('Add an Item'),
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => const ShopFormPage(),
                  ));
            },
          ),
          ListTile(
            leading: const Icon(Icons.add_shopping_cart),
            title: const Text('Show Items'),
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => const ShowItem(),
                  ));
            },
          ),
        ],
      ),
    );
  }
}

```
<br>

5. Selanjutnya, saya membuat `menu_card.dart` pada direktori `lib/widgets/` sebagai berikut.
```dart
import 'package:flutter/material.dart';
import 'package:marketplace/screens/marketplace_form.dart';
import 'package:marketplace/screens/marketplace_show.dart';

class ShopItem {
  final String name;
  final IconData icon;
  final Color color;

  ShopItem(this.name, this.icon, this.color);
}

class Items {
  final String name;
  final int price;
  final String description;

  Items({required this.name, required this.price, required this.description});
}

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
                content: Text("You have pressed the ${item.name} button!")));

          if (item.name == "Add an Item") {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => const ShopFormPage()),
            );
          }

          if (item.name == "Show Items") {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => const ShowItem()),
            );
          }
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
<br>

6. Lalu, saya membuat `marketplace_form.dart` pada direktori `lib/screens/` seperti berikut.
```dart
import 'package:flutter/material.dart';
import 'package:marketplace/widgets/left_drawer.dart';
import 'package:marketplace/widgets/menu_card.dart';

List<Items> items = [];

class ShopFormPage extends StatefulWidget {
  const ShopFormPage({super.key});

  @override
  State<ShopFormPage> createState() => _ShopFormPageState();
}

class _ShopFormPageState extends State<ShopFormPage> {
  final _formKey = GlobalKey<FormState>();

  String _name = "";
  int _price = 0;
  String _description = "";

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Center(
          child: Text(
            'Add Item Form',
          ),
        ),
        backgroundColor: Colors.lightGreen,
        foregroundColor: Colors.white,
      ),

      drawer: const LeftDrawer(),

      body: Form(
        key: _formKey,
        child: SingleChildScrollView(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Item Name",
                    labelText: "Item Name",
                    border: OutlineInputBorder(
                      borderRadius: BorderRadius.circular(5.0),
                    ),
                  ),
                  onChanged: (String? value) {
                    setState(() {
                      _name = value!;
                    });
                  },
                  validator: (String? value) {
                    if (value == null || value.isEmpty) {
                      return "Name cannot be empty!";
                    }
                    return null;
                  },
                ),
              ),

              Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Price",
                    labelText: "Price",
                    border: OutlineInputBorder(
                      borderRadius: BorderRadius.circular(5.0),
                    ),
                  ),
                  onChanged: (String? value) {
                    setState(() {
                      _price = int.parse(value!);
                    });
                  },
                  validator: (String? value) {
                    if (value == null || value.isEmpty) {
                      return "Price must not be empty!";
                    }
                    if (int.tryParse(value) == null) {
                      return "Price must be numbers!";
                    }
                    return null;
                  },
                ),
              ),

              Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Description",
                    labelText: "Description",
                    border: OutlineInputBorder(
                      borderRadius: BorderRadius.circular(5.0),
                    ),
                  ),
                  onChanged: (String? value) {
                    setState(() {
                      _description = value!;
                    });
                  },
                  validator: (String? value) {
                    if (value == null || value.isEmpty) {
                      return "The description cannot be empty!";
                    }
                    return null;
                  },
                ),
              ),

              Align(
                alignment: Alignment.bottomCenter,
                child: Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: ElevatedButton(
                    style: ButtonStyle(
                      backgroundColor:
                          MaterialStateProperty.all(Colors.lightGreen),
                    ),
                    onPressed: () {
                      if (_formKey.currentState!.validate()) {
                        items.add(Items(
                          name: _name,
                          price: _price,
                          description: _description,
                        ));

                        showDialog(
                          context: context,
                          builder: (context) {
                            return AlertDialog(
                              title: const Text('Item saved successfully'),
                              content: SingleChildScrollView(
                                child: Column(
                                  crossAxisAlignment: CrossAxisAlignment.start,
                                  children: [
                                    Text('Name: $_name'),
                                    Text('Price: $_price'),
                                    Text('Description: $_description'),
                                  ],
                                ),
                              ),
                              actions: [
                                TextButton(
                                  child: const Text('OK'),
                                  onPressed: () {
                                    Navigator.pop(context);
                                  },
                                ),
                              ],
                            );
                          },
                        );
                        _formKey.currentState!.reset();
                      }
                    },
                    child: const Text(
                      "Save",
                      style: TextStyle(color: Colors.white),
                    ),
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```
<br>

7. Kemudian, saya membuat `marketplace_show.dart` pada direktori `lib/screens/` seperti berikut.
```dart
import 'package:flutter/material.dart';
import 'package:marketplace/widgets/left_drawer.dart';
import 'package:marketplace/screens/marketplace_form.dart';
import 'package:marketplace/widgets/menu_card.dart';

class ShowItem extends StatefulWidget {
  const ShowItem({super.key});

  @override
  State<StatefulWidget> createState() => _ShowItemPage();
}

class _ShowItemPage extends State<ShowItem> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(

      appBar: AppBar(
        title: const Text('Items'),
        backgroundColor: Colors.pink,
        foregroundColor: Colors.white,
      ),

      drawer: const LeftDrawer(),
      body: ListView.builder(
        itemCount: items.length,
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(items[index].name),
            subtitle: Text(
                "Price: ${items[index].price} \nDescription: ${items[index].description}"),
            onTap: () {
            },
          );
        },
      ),
    );
  }
}
```
<br>



# BONUS
sudah diimplementasi 

Referensi:
https://ngasturi.id/2020/01/04/flutter-navigasi-antar-halaman/
https://medium.com/komandro-ccit-ftui/tutorial-flutter-layout-be8cfb66904a

</details>

<details>
<summary>Tugas 9</summary>
    
# Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?
Pengambilan data JSON tanpa membuat model itu dapat dilakukan. Pada Flutter, kita dapat menggunakan metode `json.decode` untuk mengurai *string* JSON menjadi objek `Map<String, dynamic>` dan mengakses *value* dengan menggunakan *keys*. 

Namun, jika kita mengambil data JSON dengan membuat modelnya terlebih dahulu itu akan lebih unggul dan praktis. Kelas model dapat menyediakan berbagai tipe keamanan, validasi, dan keterbacaan untuk data JSON. Selain itu, dapat membantu terhindar dari kesalahan atau bug yang terjadi saat mengakses data JSON tanpa kelas model. 
<br>

*Source:*
* https://stackoverflow.com/questions/75638056/how-to-parse-json-data-without-model-class-in-flutter-and-get-single-value
* https://blog.logrocket.com/dihttps://stackoverflow.com/questions/68343117/json-request-without-model-binding-in-asp-net-core-webapi
<br>

# Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
Fungsi CookieRequest adalah untuk menangani pengiriman dan penerimaan *cookie* dalam permintaan HTTP di Flutter. 

*Instance* CookieRequest perlu dibagian ke semua komponen dalam Flutter karena *instance* tersebut menjaga objek *CookieJar* yang menyimpan semua *cookie* untuk domain dan jalur berbeda. Dengan berbagi *instance* CookieRequest yang sama, komponen yang berbeda dapat mengakses *cookie* yang sama dan menghindar pembuatan *cookie* konflik atau duplikat.
<br>

*Source:*
* https://stackoverflow.com/questions/52500575/post-request-with-cookies-in-flutter
* https://codewithflutter.com/how-do-i-make-an-http-request-using-cookies-on-flutter/
<br>
# Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.
1. Pertama, saya membuat file baru pada folder `lib/screens` dengan nama `list_item.dart` dan menjalankan perintah di terminal Flutter seperti berikut.
```bash
flutter pub add http
```
<br>

2. Kedua, saya mengimpor *library* yang dibutuhkan di `list_item.dart` seperti berikut.
```dart
import 'package:flutter/material.dart';
import 'package:http/http.dart' as http;
import 'dart:convert';
import 'package:marketplace/models/item.dart';
import 'package:marketplace/screens/show_item.dart';
import 'package:marketplace/widgets/left_drawer.dart';
```
<br>

3. Ketiga, saya membuat fungsi untuk mengambil data dari server dengan mengirimkan GET Request ke URL dengan potongan kode seperti berikut.
```dart
var url = Uri.parse('http://127.0.0.1:8000/get-product/');
    var response = await http.get(
      url,
      headers: {"Content-Type": "application/json"},
    );
```
<br>

4. Keempat, saya mengambil respons dari permintaan HRRP dengan mengkonversi *string* JSON seperti berikut.
```dart
  var data = jsonDecode(utf8.decode(response.bodyBytes));
```
<br>
5. Kelima, saya membuat `list` bernama `listItem` untuk membuat objek *item* dengan menggunakan data JSON seperti berikut.
```dart
    List<Product> listItem = [];
    for (var d in data) {
      if (d != null) {
        listItem.add(Product.fromJson(d));
      }
    }
    return listItem;
```
<br>

6. keenam, saya membuat halaman untuk menampilkan daftar *item* dan memberikan kemampuan navigasi ke halaman *detail item* ketika pengguna mengklik salah satu *item* dalam daftar dengan kode seperti berikut.
```dart
@override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Items'),
        backgroundColor: Colors.pink,
        foregroundColor: Colors.white,
      ),
      drawer: const LeftDrawer(),
      body: FutureBuilder(
        future: fetchProduct(),
        builder: (context, AsyncSnapshot snapshot) {
          if (snapshot.data == null) {
            return const Center(child: CircularProgressIndicator());
          } else {
            if (!snapshot.hasData) {
              return const Column(
                children: [
                  Text(
                    "No item data.",
                    style: TextStyle(color: Color(0xff59A5D8), fontSize: 20),
                  ),
                  SizedBox(height: 8),
                ],
              );
            } else {
              return ListView.builder(
                itemCount: snapshot.data!.length,
                itemBuilder: (_, index) => Column(
                  children: [
                    GestureDetector(
                      onTap: () {
                        Navigator.push(
                          context,
                          MaterialPageRoute(
                            builder: (context) => DetailProductPage(
                              product: snapshot.data![index],
                            ),
                          ),
                        );
                      },
                      child: Container(
                        margin: const EdgeInsets.symmetric(
                            horizontal: 16, vertical: 12),
                        padding: const EdgeInsets.all(20.0),
                        child: Column(
                          mainAxisAlignment: MainAxisAlignment.start,
                          crossAxisAlignment: CrossAxisAlignment.start,
                          children: [
                            Text(
                              "${snapshot.data![index].fields.name}",
                              style: const TextStyle(
                                fontSize: 18.0,
                                fontWeight: FontWeight.bold,
                              ),
                            ),
                          ],
                        ),
                      ),
                    ),
                    if (index < snapshot.data!.length - 1) const Divider(),
                  ],
                ),
              );
            }
          }
        },
      ),
    );
  }
```
<br>

# Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
1. Pertama, saya membuat metode *view* untuk login pada `authentication/views.py` seperti berikut.
```python
@csrf_exempt
def login(request):
    username = request.POST['username']
    password = request.POST['password']
    user = authenticate(username=username, password=password)
    if user is not None:
        if user.is_active:
            auth_login(request, user)
            # Status login sukses.
            return JsonResponse({
                "username": user.username,
                "status": True,
                "message": "Login sukses!"
            }, status=200)
        else:
            return JsonResponse({
                "status": False,
                "message": "Login gagal, akun dinonaktifkan."
            }, status=401)

    else:
        return JsonResponse({
            "status": False,
            "message": "Login gagal, periksa kembali email atau kata sandi."
        }, status=401)
```
<br>

2. Kedua, saya nenbuat file `urls.py` pada folder `authentication` dan menambahkan URL *routing* seperti berikut.
```python
from django.urls import path
from authentication.views import login

app_name = 'authentication'

urlpatterns = [
    path('login/', login, name='login'),
]
```
<br>

3. Ketiga, saya menambahkan `path('auth/', include('authentication.urls')),` pada file `shopping_list/urls.py`.
<br>
4. keempat, saya membuat file baru bernama `login.dart` di folder `screens`.
<br>

5. Kelima, saya menginstal *package* yang telah disediakan dan menjalankannya di terminal seperti berikut.
```bash
flutter pub add provider
flutter pub add pbp_django_auth
```
<br>
6. Keenam, saya mengubah `main.dart` saya menjadi seperti berikut.
```dart
import 'package:flutter/material.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';
import 'package:marketplace/screens/login.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Provider(
      create: (_) {
        CookieRequest request = CookieRequest();
        return request;
      },
      child: MaterialApp(
        title: 'Flutter App',
        theme: ThemeData(
          colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
          useMaterial3: true,
        ),
        home: const LoginPage(),
      ),
    );
  }
}

```
<br>

7. Terakhir, saya mengubah `home: MyHomePage()` menjadi `home: LoginPage()` pada `main.dart`.
<br>

# Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.

| Nama *Widget* | Fungsi |
| --- | --- |
| `AppBar` | Untuk menampilkan bilah atas pada halaman, yaitu `marketplace` |
| `Scaffold` | Untuk kerangka utama dari halaman, yang mencakup `AppBar` dan `Body` |
| `Column` | Untuk mengatur *widget-children* secara vertikal |
| `SnackBar` | Untuk menampilkan pesan singkat yang muncul di bawah layar saat item toko diklik |
| `ListView.Builder` | Untuk membuat daftar dengan elemen-elemen yang dibuat secara dinamis berdasarkan data atau model tertentu |
| `TextField` | Untuk menginput teks dari *user* |
| `Container` | Untuk mengelola tata letak dan konten dalam *card* |
| `Navigator` | Untuk menavigasi ke halaman baru dan menggantikan halaman tersebut |
| `FutureBuilder` | Untuk menangani proses pengembalian data yang bersifat asinkron, yaitu mengambil dan menampilkan data *item* dengan menunggu fungsi `fetchProduct()` |
<br>

# Implementasi checklisst

# Mengintegrasikan Sistem Autentikasi Django dengan Flutter
1. Pertama, saya membuat `django-app` bernama `authentication` pada proyek Django `shopping_list`.
<br>

2. Lalu, saya menambahkan `authentication` ke `INSTALLED_APPS` pada *main project* `settings.py` Django.
<br>

3. Kemudian, saya menjalankan perintah `pip install django-cors-headers` untuk menginstal *library* yang dibutuhkan.
<br>

4. Lalu, saya menambahkan `corsheaders` ke `INSTALLED_APPS` pada *main project* `settings.py` Django.
<br>

5. Selanjutnya, saya menambahkan `corsheaders.middleware.CorsMiddleware` pada *main project* `settings.py` Django.
<br>

6. Lanjut, saya menambahkan beberapa variabel pada *main project* `settings.py` Django seperti berikut.
```python
CORS_ALLOW_ALL_ORIGINS = True
CORS_ALLOW_CREDENTIALS = True
CSRF_COOKIE_SECURE = True
SESSION_COOKIE_SECURE = True
CSRF_COOKIE_SAMESITE = 'None'
SESSION_COOKIE_SAMESITE = 'None'
```
<br>

# Membuat halaman Login pada Flutter
1. Pertama, saya membuat metode *view* untuk login pada `authentication/views.py`.
<br>

2. Kedua, saya nenbuat file `urls.py` pada folder `authentication` dan menambahkan URL *routing*.
<br>

4. keempat, saya membuat file baru bernama `login.dart` di folder `screens`.
<br>

5. Kelima, saya menginstal *package* yang telah disediakan dan menjalankannya di terminal seperti berikut.
```bash
flutter pub add provider
flutter pub add pbp_django_auth
```
<br>
6. Keenam, saya memodifikasi `main.dart` saya dan mengubah `home: MyHomePage()` menjadi `home: LoginPage()`.
<br>

# Membuat Model Kustom sesuai Django
1. Pertama, saya membuka *endpoint* `JSON` yang sudah dibuat pada Tutorial 2.
<br>

2. Selanjutnya, saya menyalin data `JSON` dan membuka situs web Quicktype.
<br>

3. Pada situs tersebut, saya mengubah *setup name* menjadi `Product`, *source type* menjadi `JSON`, dan *language* menjadi `Dart`.
<br>

4. Lalu, saya menempelkan data JSON yang sudah disalin ke dalam *textbox* yang ada pada Quicktype.
<br>

5. Kemudian, saya mengklik pilihan `Copy Code` pada Quicktype.
<br>

6. Setelah mendapatkan kode model dari Quicktype, saya membuka proyek Flutter dan membuat file baru pada folder `lib/models` dengan nama `item.dart` dan menempelkan kode yang disalin dari Quicktype.
<br>

# Membuat Halaman Berisi Detail Item
1. Pertama, saya membuat file baru bernama `show_item.dart` yang ada di `lib/screens` seperti berikut.
```dart
import 'package:flutter/material.dart';
import 'package:marketplace/models/item.dart';

class DetailProductPage extends StatelessWidget {
  final Product product;
  const DetailProductPage({Key? key, required this.product}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(product.fields.name),
        backgroundColor: Colors.pink,
        foregroundColor: Colors.white,
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: <Widget>[
            Text(
              product.fields.name,
              style: const TextStyle(
                fontSize: 22,
                fontWeight: FontWeight.bold,
              ),
            ),
            const SizedBox(height: 20),
            Text('Price: ${product.fields.price}'),
            const SizedBox(height: 20),
            Text('Description: ${product.fields.description}'),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () {
          Navigator.pop(context);
        },
        backgroundColor: Colors.pink,
        foregroundColor: Colors.white,
        child: const Icon(Icons.arrow_back),
      ),
    );
  }
}

```
<br>
2. Kemudian, saya mengimpor `'package:marketplace/screens/show_item.dart';` di file `list_item.dart` dan menambahkan beberapa kode yang mengarahkan ke `show_item.dart` dengan potongan kode seperti berikut.
```dart
return ListView.builder(
                itemCount: snapshot.data!.length,
                itemBuilder: (_, index) => Column(
                  children: [
                    GestureDetector(
                      onTap: () {
                        Navigator.push(
                          context,
                          MaterialPageRoute(
                            builder: (context) => DetailProductPage(
                              product: snapshot.data![index],
                            ),
                          ),
                        );
                      },
                    ),
                  ],
                ),
      ...
),
...
```
<br>

3. Terakhir, saya melakukan `add`, `commit`, `push` pada repositori `marketplace` di GitHub.
<br>

# Bonus
Bonus sudah saya implementasikan sesuai ketentuan, yaitu membuat `register.dart` dan filter data *item* dari *user*.
<br>
</details>
