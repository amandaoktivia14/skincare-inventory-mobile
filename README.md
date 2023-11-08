# skincare_inventory

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

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
          // Memunculkan SnackBar ketika diklik
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