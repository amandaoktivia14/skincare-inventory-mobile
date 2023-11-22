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
 
Contoh penerapan:

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

1. **TextFormField untuk Nama:**
   - Input ini digunakan untuk memasukkan nama produk skincare.
   - Validasi memastikan bahwa nama tidak boleh kosong dan harus terdiri dari huruf, bukan angka, karena nama biasanya berisi karakter alfabet.

2. **TextFormField untuk Jumlah:**
   - Input ini digunakan untuk memasukkan jumlah produk yang tersedia.
   - Validasi pada input ini memastikan bahwa jumlah tidak boleh kosong dan harus berupa angka, yang penting untuk manajemen inventaris produk.

3. **TextFormField untuk Deskripsi:**
   - Input ini digunakan untuk memasukkan deskripsi produk skincare.
   - Ini memungkinkan teks bebas namun memastikan bahwa deskripsi tidak boleh kosong dan tidak boleh berupa angka, karena deskripsi harus berisi kalimat atau frase yang menjelaskan produk dengan baik.

4. **TextFormField untuk Gambar:**
   - Input ini digunakan untuk memasukkan URL gambar produk skincare.
   - Validasi memastikan bahwa bidang ini tidak boleh kosong dan memeriksa bahwa inputan adalah URL yang valid.

5. **TextFormField untuk Harga:**
   - Input ini digunakan untuk memasukkan harga produk skincare.
   - Seperti input jumlah, ini harus berupa angka dan tidak boleh kosong, yang penting untuk penentuan harga produk.

6. **TextFormField untuk Kategori:**
   - Input ini digunakan untuk memasukkan kategori produk skincare.
   - Validasi memastikan bahwa kategori tidak boleh kosong dan harus berupa kata atau frasa yang sesuai dengan kategori produk.

Selain itu, ada sebuah tombol ElevatedButton yang digunakan untuk mengirimkan form setelah semua validasi terpenuhi. Ketika tombol ditekan, form akan memvalidasi inputan, dan jika semuanya benar, informasi produk akan disimpan ke daftar produk dan menampilkan dialog konfirmasi.

Semua elemen input ini dipilih karena mereka memungkinkan pengguna untuk memasukkan berbagai jenis data yang diperlukan untuk menciptakan entri produk yang lengkap dan valid. Validasi pada setiap bidang memastikan bahwa data yang dimasukkan sesuai dengan tipe data yang diperlukan untuk setiap atribut produk.

>4. Bagaimana penerapan clean architecture pada aplikasi Flutter?

 Dalam konteks Flutter, penerapan clean architecture melibatkan penggunaan konsep seperti Entities, Use Cases, dan Interface Adapters. 
 1. **Entities:** merepresentasikan objek domain atau model bisnis
 2. **Use Cases:** berisi aturan bisnis
 3. **Interface Adapters:** bertanggung jawab untuk menghubungkan bagian-bagian sistem seperti database atau UI dengan core business logic. 

Penerapan clean architecture pada Flutter juga memungkinkan penggunaan pola desain seperti BLoC (Business Logic Component) untuk mengelola state dan logika aplikasi, pola desain ini memungkinkan pemisahan antara tampilan dan logika bisnis, sehingga memudahkan pengujian dan pemeliharaan kode.  

>5. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)

1. Membuat minimal satu halaman baru pada aplikasi, yaitu halaman formulir tambah item baru

2. Mengarahkan pengguna ke halaman form tambah item baru ketika menekan tombol Tambah Item pada halaman utama.

3. Memunculkan data sesuai isi dari formulir yang diisi dalam sebuah pop-up setelah menekan tombol Save pada halaman formulir tambah item baru.

4. Membuat sebuah drawer pada aplikasi dengan ketentuan sebagai berikut: Drawer minimal memiliki dua buah opsi, yaitu Halaman Utama dan Tambah Item, Ketika memiih opsi Halaman Utama, maka aplikasi akan mengarahkan pengguna ke halaman utama, Ketika memiih opsi (Tambah Item), maka aplikasi akan mengarahkan pengguna ke halaman form tambah item baru.


## Tugas 9: Integrasi Layanan Web Django dengan Aplikasi Flutter

>1. Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?

Tentu, dalam pengembangan aplikasi Flutter, ada opsi untuk mengambil data dalam format JSON tanpa harus membuat model terlebih dahulu. Data JSON ini dapat diambil dan dikelola langsung dalam bentuk `Map<String, dynamic>` atau `List<Map<String, dynamic>>`, tergantung pada struktur data JSON yang diterima. Meskipun memungkinkan, pendekatan ini mungkin tidak selalu merupakan pilihan yang paling ideal, dan ada beberapa alasan untuk mempertimbangkan penggunaan model:

**1. Ketidakefisienan:** Mengelola data JSON langsung memerlukan penanganan manual untuk setiap field data, yang dapat menjadi rumit dan rawan kesalahan. Penggunaan model memungkinkan Anda untuk mengatur struktur data dengan lebih baik.

**2. Ketidakrapihan Kode:** Ketika Anda bekerja dengan data JSON secara langsung, kode Anda mungkin menjadi kurang rapi dan sulit dibaca karena Anda harus melakukan banyak mapping manual. Model membantu menjaga kebersihan dan keterbacaan kode.

**3. Ketidakamanan Tipe Data:** Tanpa model, tidak ada jaminan keamanan tipe data. Kesalahan tipe data dapat terjadi karena struktur data JSON hanya diketahui pada saat runtime. Dengan model, Anda dapat memastikan keamanan tipe data.

**4. Skalabilitas dan Pemeliharaan:** Dengan penggunaan model, memperbarui atau mengubah struktur data menjadi lebih mudah dan terpusat. Ini memungkinkan Anda untuk memelihara dan mengembangkan aplikasi dengan lebih efisien.

Berikut adalah perbandingan antara pengambilan data JSON tanpa membuat model terlebih dahulu dan penggunaan model:

| Aspek                       | Tanpa Model                                     | Dengan Model                                    |
|-----------------------------|-------------------------------------------------|-------------------------------------------------|
| Ketidakefisienan            | Tinggi, memerlukan penanganan manual            | Rendah, model mengelola struktur data            |
| Ketidakrapihan Kode         | Kode kurang rapi dan sulit dibaca               | Kode lebih rapi dan mudah dibaca                |
| Ketidakamanan Tipe Data    | Tinggi, keamanan tipe data tidak terjamin       | Rendah, model menyediakan keamanan tipe data    |
| Skalabilitas dan Pemeliharaan | Rendah, sulit memperbarui atau mengubah struktur data | Tinggi, mudah memperbarui atau mengubah struktur data |

Dalam banyak kasus, menggunakan model untuk mengelola data adalah praktik yang lebih baik, terutama dalam pengembangan aplikasi yang lebih besar atau kompleks. Ini membantu meningkatkan kualitas, keamanan, dan keterbacaan kode aplikasi Anda.

>2. Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.

`CookieRequest` adalah sebuah kelas yang digunakan untuk mengelola HTTP requests dalam konteks aplikasi Flutter sambil menjaga dan mengelola cookies. Hal ini memiliki peran penting dalam menjaga autentikasi dan sesi yang berkelanjutan dalam aplikasi. Berikut adalah deskripsi tentang fungsionalitas dan kebutuhan dari instance `CookieRequest` dalam aplikasi Flutter:

**Fungsi dan Kebutuhan dari Instance `CookieRequest` dalam Aplikasi Flutter:**

| Aspek               | Keterangan                                                         |
|---------------------|-------------------------------------------------------------------|
| Mengelola Cookies   | Bertugas untuk mengelola cookies yang diperlukan dalam setiap permintaan (request) dan respon HTTP. Cookies ini penting dalam menyimpan informasi autentikasi dan sesi.                        |
| Persistensi Sesi    | Memungkinkan aplikasi untuk menjaga sesi pengguna tetap aktif selama aplikasi tetap terbuka. Ini penting agar pengguna tidak harus melakukan autentikasi ulang setiap saat. |
| Konsistensi Sesi    | Menjaga konsistensi dalam sesi pengguna dengan memastikan bahwa setiap permintaan yang dilakukan dalam konteks sesi tertentu tetap menggunakan sesi yang sama.        |
| Efisiensi           | Menghindari pembuatan instance `CookieRequest` yang berlebihan. Hal ini membantu dalam meminimalkan penggunaan sumber daya dan mempertahankan efisiensi aplikasi. |

Dengan menggunakan `CookieRequest`, aplikasi Flutter dapat dengan efektif mengelola cookies, mempertahankan sesi pengguna, dan memastikan konsistensi dalam setiap permintaan HTTP. Hal ini sangat berguna dalam konteks autentikasi dan menjaga pengalaman pengguna yang konsisten dalam aplikasi Anda.

>3. Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.

Cara-cara untuk mengambil data dari JSON dan menampilkannya di dalam aplikasi Flutter melibatkan beberapa langkah penting:

1. Mengambil Data:
   - Lakukan HTTP request, biasanya dengan metode GET, untuk mengambil data JSON dari layanan web.
   
2. Mengubah Data JSON menjadi Objek Dart:
   - Terjemahkan data JSON yang diterima menjadi objek Dart. Ini dapat dilakukan dengan cara:
     - Menggunakan model Dart yang telah dibuat sebelumnya yang sesuai dengan struktur JSON.
     - Mengonversi data JSON secara langsung menjadi Map atau List, bergantung pada struktur JSON yang ada.
   
3. Pemanfaatan Data:
   - Gunakan data yang telah diubah menjadi objek Dart untuk mengisi state atau variabel dalam aplikasi Flutter. Data ini dapat digunakan baik untuk tampilan langsung maupun untuk logika tambahan di dalam aplikasi.
   
4. Menampilkan Data:
   - Tampilkan data yang telah diubah dalam aplikasi menggunakan berbagai widget yang disediakan oleh Flutter. Sebagai contoh:
     - Gunakan ListView.builder untuk menampilkan daftar data dengan cara yang efisien.
     - Gunakan widget Text atau Card untuk menampilkan detail data sesuai kebutuhan aplikasi.

Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah mengintegrasikan data JSON ke dalam aplikasi Flutter Anda dan menampilkannya sesuai dengan kebutuhan.

>4. Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.

Proses autentikasi antara aplikasi Flutter dan backend Django melibatkan serangkaian langkah penting untuk memastikan keamanan dan kelancaran pertukaran data.

1. Input Data Pengguna:
   - Pengguna mengisi data akun mereka, seperti username dan password, di dalam aplikasi Flutter.

2. Pengiriman ke Django:
   - Aplikasi Flutter mengirimkan data akun ini ke backend Django menggunakan HTTP request, yang umumnya menggunakan metode POST.

3. Proses di Django:
   - Backend Django menerima data yang dikirimkan dan melakukan proses autentikasi. Ini mencakup pemeriksaan data pengguna dengan database untuk memastikan kesesuaian.

4. Respon Kembali ke Flutter:
   - Setelah selesai memproses data, Django mengirimkan respons kembali ke aplikasi Flutter. Respons ini bisa berupa konfirmasi keberhasilan autentikasi atau pemberitahuan kegagalan autentikasi.

5. Tampilan di Flutter:
   - Berdasarkan respons yang diterima dari Django, aplikasi Flutter kemudian menampilkan hasil autentikasi kepada pengguna. Jika autentikasi berhasil, mungkin akan membuka halaman menu utama atau dashboard. Namun, jika autentikasi gagal, aplikasi mungkin akan menampilkan pesan kesalahan atau meminta pengguna untuk mencoba lagi.

Dengan mengikuti langkah-langkah ini, Anda dapat memastikan bahwa proses autentikasi antara aplikasi Flutter dan backend Django berjalan dengan aman dan efisien.

>5. Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.

Widget yang digunakan dalam tugas ini dan peran masing-masing adalah sebagai berikut:

1. Scaffold: 
   - Berfungsi untuk membentuk kerangka dasar tampilan aplikasi, termasuk app bar, body, dan bottom navigation jika diperlukan.

2. ListView.builder:
   - Digunakan untuk membuat daftar elemen secara dinamis berdasarkan data yang diberikan. Ini memungkinkan tampilan daftar yang efisien dan hanya membangun elemen yang terlihat.

3. TextFormField:
   - Berperan dalam mengumpulkan input teks dari pengguna. Ini adalah widget yang ideal untuk mengambil data masukan seperti teks, email, atau password.

4. ElevatedButton:
   - Merupakan tombol yang digunakan untuk menginisiasi tindakan tertentu, seperti mengirimkan formulir. Ini memudahkan pengguna untuk berinteraksi dengan aplikasi dengan melakukan tindakan spesifik.

5. FutureBuilder:
   - Mengambil hasil dari interaksi dengan Future (biasanya dalam bentuk permintaan jaringan atau pemrosesan data asinkron). Widget ini memungkinkan pembangunan UI yang dinamis berdasarkan hasil yang diambil dari Future, memungkinkan tampilan yang responsif sesuai dengan proses yang sedang berlangsung.

Dengan memahami peran masing-masing widget ini, Anda dapat merancang tampilan aplikasi Flutter Anda dengan lebih baik dan meningkatkan fungsionalitasnya sesuai dengan kebutuhan proyek Anda.