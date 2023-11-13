# skincare_inventory
A new Flutter project.

## Tugas 7: Elemen Dasar Flutter

>1. Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?

Perbedaan utama antara Stateless dan stateful widget adalah dalam cara mereka mengelola dan mempertahankan keadaan (state) aplikasi.

- [x] Stateless widget:
- Tidak menyimpan keadaan internal.
- Hanya menggambarkan tampilan berdasarkan input yang diberikan.
- Tidak memiliki keadaan yang berubah seiring waktu dan tidak dapat memperbarui tampilan secara dinamis.
- Dibangun ulang dari awal setiap kali ada perubahan pada input.
- Cocok digunakan untuk tampilan statis yang tidak memerlukan pembaruan berkelanjutan.

- [x] Stateful widget:
- Dapat menyimpan dan mempertahankan keadaan internal.
- Memungkinkan pembaruan tampilan secara dinamis berdasarkan perubahan keadaan.
- Memiliki metode build yang dipanggil ketika ada perubahan pada keadaan, sehingga memungkinkan pembaruan tampilan yang responsif.
- Keadaan internal stateful widget dapat berubah seiring waktu dan dapat diperbarui dengan menggunakan metode setState().
- Cocok digunakan untuk tampilan yang memerlukan pembaruan berkelanjutan, seperti formulir interaktif atau animasi.

>2. Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.

1. `MyApp` (Stateless Widget):
   - Merupakan root widget dari aplikasi Anda.
   - Digunakan untuk mengatur tema (theme) dan halaman utama (home) aplikasi.

2. `MaterialApp` (Widget):
   - Mewakili aplikasi Flutter dan mengatur konfigurasi global seperti judul aplikasi dan tema.
   - Widget ini memberikan komponen seperti `Scaffold` dan `AppBar` untuk membangun antarmuka pengguna.

3. `MyHomePage` (Stateless Widget):
   - Merupakan halaman utama aplikasi yang menampilkan daftar item (ShopItem).
   - Menggunakan `Scaffold` untuk mengatur tata letak halaman.

4. `AppBar` (Widget):
   - Menampilkan bilah aplikasi di bagian atas halaman dengan judul "Skincare Inventory Page".
   - Anda mengatur latar belakangnya ke warna `Colors.indigo` dan teksnya ke warna putih.

5. `SingleChildScrollView` (Widget):
   - Mengelilingi tampilan halaman utama, memungkinkan kontennya untuk discroll jika melebihi ukuran layar.

6. `GridView.count` (Widget):
   - Digunakan untuk membuat tampilan grid yang menampilkan daftar item (ShopItem).
   - Anda dapat mengatur jumlah kolom dan elemen-elemen dari `items`.

7. `ShopItem` (Model Class):
   - Kelas model yang berisi informasi tentang setiap item, termasuk nama, ikon, dan warna latar belakang.
   - Merepresentasikan data yang akan digunakan untuk membuat `ShopCard`.

8. `ShopCard` (Stateless Widget):
   - Merupakan kartu yang menampilkan setiap item di dalam grid.
   - Menggunakan `Material` untuk memberikan latar belakang berwarna sesuai dengan warna item.
   - Menggunakan `InkWell` agar merespons ketika ditekan dan menampilkan `SnackBar` ketika di-tap.
   - Berisi ikon dan teks yang sesuai dengan item yang diberikan.

9. Berbagai widget dalam `MyHomePage` seperti `Padding`, `Column`, `Text`, `Icon`, `Container`, dan sebagainya digunakan untuk merancang tampilan halaman utama dengan pemformatan yang sesuai.

>3. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).
1. Buat website flutter baru dengan tema inventory dengan langkah-langkah seperti pada tutorial 6.
2. Buat tiga tombol sederhana (Lihat item, Tambah item, dan Logout).

        final List<ShopItem> items = [
            ShopItem("Lihat Item", Icons.checklist, Colors.green),
            ShopItem("Tambah Item", Icons.add_shopping_cart, Colors.red),
            ShopItem("Logout", Icons.logout, Colors.yellow),
        ];

3. Memunculkan snackbar ketika ketiga tombol tersebut ditekan. 

        onTap: () {
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));

4. BONUS (mengimplementasikan warna-warna yang berbeda untuk setiap tombol (Lihat Item, Tambah Item, dan Logout).
        
        final List<ShopItem> items = [
            ShopItem("Lihat Item", Icons.checklist, Colors.green),
            ShopItem("Tambah Item", Icons.add_shopping_cart, Colors.red),
            ShopItem("Logout", Icons.logout, Colors.yellow),
        ];

        class ShopItem {
            final String name;
            final IconData icon;
            final Color color; //tambahkan property color

            ShopItem(this.name, this.icon, this.color);
        }

        @override
        Widget build(BuildContext context) {
            return Material(
                color: item.color, //warna dari properti ShopItem
                //...


## Tugas 8: Flutter Navigation, Layouts, Forms, and Input Elements

 >1. Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!

Navigator.push() dan Navigator.pushReplacement() adalah metode navigasi yang digunakan dalam pengembangan aplikasi Flutter. Berikut penjelasan mengenai perbedaan kedua metode tersebut serta penerapannya. 

- [x] Navigator.push() 
digunakan untuk menambahkan route baru ke navigator stack (memungkinkan pengguna untuk berpindah ke layar baru sambil tetap mempertahankan layar sebelumnya di memori).

- [x] Navigator.pushReplacement() 
menggantikan route saat ini dalam navigator stack dengan route baru, efektif menghapus route saat ini dari stack (ketika menggunakan Navigator.pushReplacement(), pengguna tidak dapat kembali ke layar sebelumnya menggunakan tombol kembali, karena layar sebelumnya dihapus dari stack).  
 
Contoh:

   dalam sebuah aplikasi Flutter, jika pengguna perlu berpindah dari Layar A ke Layar B, dan kemudian dari Layar B ke Layar C, menggunakan Navigator.push() akan menambahkan Layar C ke stack yang memungkinkan pengguna untuk kembali ke Layar B. 
   
   Namun, jika Navigator.pushReplacement() digunakan untuk berpindah dari Layar B ke Layar C, Layar B akan digantikan oleh Layar C dalam stack, dan pengguna tidak akan dapat kembali ke Layar B.  
 

>2. Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!

1. **Row Widget:**
   - Konteks Penggunaan: untuk penempatan widget berdampingan, seperti ikon atau teks horizontal.

2. **Column Widget:**
   - Konteks Penggunaan: untuk penempatan widget berurutan dari atas ke bawah.

3. **Stack Widget:**
   - Konteks Penggunaan: untuk penempatan widget di atas satu sama lain, seperti overlay teks di atas gambar.

4. **Expanded Widget:**
   - Konteks Penggunaan: memberi ukuran seimbang atau proporsional dalam widget Row atau Column.

5. **ListView Widget:**
   - Konteks Penggunaan: untuk menampilkan daftar data dinamis.

6. **GridView Widget:**
   - Konteks Penggunaan: untuk menampilkan koleksi data dalam format grid.

7. **Flexible Widget:**
   - Konteks Penggunaan: untuk memberikan proporsi tertentu dari ruang yang tersedia kepada widget dalam tata letak fleksibel.


>3. Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!

>4. Bagaimana penerapan clean architecture pada aplikasi Flutter?

 Dalam konteks Flutter, penerapan clean architecture melibatkan penggunaan konsep seperti Entities, Use Cases, dan Interface Adapters. 
 1. **Entities:** merepresentasikan objek domain atau model bisnis
 2. **Use Cases:** berisi aturan bisnis
 3. **Interface Adapters:** bertanggung jawab untuk menghubungkan bagian-bagian sistem seperti database atau UI dengan core business logic. 

Penerapan clean architecture pada Flutter juga memungkinkan penggunaan pola desain seperti BLoC (Business Logic Component) untuk mengelola state dan logika aplikasi, pola desain ini memungkinkan pemisahan antara tampilan dan logika bisnis, sehingga memudahkan pengujian dan pemeliharaan kode.  

>5. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)