# Lab6Web - Praktikum 6: JavaScript DOM dan Event Handling

**Nama**: MUHAMMAD FACHRUDDIN  
**NIM**: 312510103  
**Mata Kuliah**: Pemrograman Web  
**Pertemuan**: 7  
**Fakultas / Program Studi**: Teknik Informatika (Universitas Pelita Bangsa)

---

## 1. Tujuan Praktikum
Praktikum ini dirancang agar mahasiswa mampu:
1. Memahami konsep **Document Object Model (DOM)** sebagai representasi struktur dokumen HTML dalam bentuk objek (tree) yang dapat diakses dan dimanipulasi oleh JavaScript.
2. Menggunakan metode seleksi elemen DOM secara presisi melalui atribut `id`, `class`, dan aturan *selector CSS* (menggunakan `getElementById`, `querySelector`, dan `querySelectorAll`).
3. Mengubah secara dinamis isi konten (seperti teks via `textContent`), atribut bawaan HTML, hingga memanipulasi susunan kelas CSS dan gaya tata letak elemen hanya melalui kode JavaScript.
4. Menangani interaksi pengguna (*Event Handling*) menggunakan antarmuka `addEventListener()`, mencakup respon terhadap klik tombol, input teks (ketikan), *submit* formulir, hingga interaksi pemilihan menu *dropdown*.
5. Merancang logika validasi form mandiri (memeriksa input kosong, panjang karakter minimal, pola regex e-mail, dan rentang batasan usia/angka numerik) serta menampilkan pesan sukses/gagal di antarmuka halaman.
6. Membangun halaman antarmuka web interaktif seutuhnya dengan mensinergikan HTML5 struktural, tampilan estetika dari CSS3, serta manipulasi dan kontrol event dari *Vanilla JavaScript*.

---

## 2. Struktur Direktori dan Penjelasan File
Repositori praktikum ini terdiri dari beberapa berkas dengan peran masing-masing:
- **`index.html`**  
  Bertindak sebagai tulang punggung (kerangka struktur) antarmuka web. File ini memuat struktur Latihan 1 hingga Latihan 6, Mini Project Form Pendaftaran Workshop, dan penerapan Eksperimen Mandiri (seperti paragraf *toggle*). Seluruh logika tidak ditulis *inline* di dalam file ini melainkan dipanggil secara eksternal.
- **`style.css`**  
  Lembar gaya (CSS) statis yang mempercantik tata letak `index.html`. Di dalam file ini terdapat gaya presentasi standar serta kelas-kelas (seperti `.highlight`, `.teks-besar`, `.selesai`, `.sembunyikan`) yang ditujukan untuk disuntikkan (*inject*) dan dicabut (*remove/toggle*) secara dinamis oleh JavaScript.
- **`script.js`**  
  *Core logic* atau pusat pengendali interaksi. Ditulis menggunakan JavaScript murni (tanpa campur tangan framework/library eksternal) dan menggunakan format karakter *plain text* ASCII. File ini menangani pencarian elemen DOM (`getElementById`), merekam event dari penekanan *mouse* dan *keyboard*, memanifestasikan antarmuka *To-do list* (`createElement`), serta merangkum sistem validasi *Real-time* form.
- **`README.md`**  
  File Markdown ini berfungsi sebagai laporan resmi komprehensif, merangkum dokumentasi repositori, panduan pengoperasian aplikasi, alur kerja/penyelesaian tugas, dan menampung daftar jawaban dari evaluasi teoretis.

---

## 3. Cara Menjalankan Program (Panduan Eksekusi)
Langkah-langkah untuk menjalankan file secara lokal (*Client-Side*):
1. Unduh dan ekstrak isi file kompresi (ZIP) repositori ini ke dalam sebuah folder (misalnya `lab6_dom_event_lengkap`).
2. Masuk ke dalam direktori hasil ekstraksi.
3. Buka (dobel klik atau seret) file `index.html` ke dalam aplikasi peramban web modern, disarankan Google Chrome, Mozilla Firefox, atau Microsoft Edge. (Tidak diperlukan server lokal seperti XAMPP atau Node.js karena file bekerja murni dari sisi klien).
4. Untuk pemantauan dan proses perunutan masalah (*debugging*), Anda dipersilakan menekan tombol **F12** untuk membuka area panel *Developer Tools* dan fokuskan pada tab **Console**.

---

## 4. Rincian Langkah Kerja (Implementasi Latihan)
Berikut adalah ulasan dari penyelesaian masalah untuk tiap-tiap nomor latihan:
* **Latihan 1 & 2 (Manipulasi Teks Sederhana & Event Klik)**  
  Menemukan elemen target menggunakan ID-nya. Saat tombol "Klik Saya" ditekan, event `click` akan aktif, lalu kode merespons dengan menyisipkan string teks yang digabung bersama pembacaan waktu *real-time* sistem komputasi (metode `toLocaleTimeString()`) ke properti `.textContent` elemen paragraf.
* **Latihan 3 (Injeksi Kelas dan Manipulasi Tampilan CSS Dinamis)**  
  Menampilkan kekuatan interaksi presentasi dengan memanfaatkan antarmuka DOM `classList.toggle()`. Fungsi tersebut akan bertindak sebagai tombol "nyala/mati", di mana jika tombol ditekan, maka ia menambahkan kelas `.highlight` dan `.teks-besar`, yang langsung memperbarui gaya kotak dan font di layar. Jika ditekan kembali, kelas tersebut dihapus.
* **Latihan 4 (Event Listener pada Input & Penghitung Real-time)**  
  Event tidak hanya bereaksi terhadap klik. Pada latihan ini, fungsi `addEventListener("input")` dipasang agar setiap kali tombol keyboard ditekan (menambah huruf/menghapus string), mesin langsung mengkalkulasi panjang string (`value.length`) lalu memperbarui jumlah angka karakter pada layar secara seketika.
* **Latihan 5 (Validasi Pendaftaran Formulir & Pencegahan Perilaku Default)**  
  Mengimplementasikan metode fundamental `event.preventDefault()` dalam struktur `addEventListener("submit")` pada *form*. Ini mencegah halaman ter-muat ulang (ter-*refresh*), sehingga kita memiliki kesempatan memverifikasi nilai *input*. Verifikasi mengecek apakah `nama` diisi dengan benar, format `email` memenuhi syarat konstruksi ekspresi reguler (Regex), dan pengkondisian rentang numerik `usia` (harus angka utuh, bernilai minimal 17 dan maksimal 100).
* **Latihan 6 (Pembuatan DOM List Dinamis — To-Do List)**  
  Struktur list tidak dirancang permanen dalam HTML. Melalui `document.createElement("li")` dan kawan-kawannya, setiap *input* tugas dibaca dan dibangun sebagai elemen *list item* baru di dalam RAM memori. Tugas-tugas ini kemudian di-*append* atau ditempelkan ke struktur dokumen `<ul id="daftarTugas">`. Setiap tugas yang ditempel, langsung disertakan tombol 'Selesai' sebagai bentuk manipulasi *toggle line-through* (coretan gaya css).

---

## 5. Implementasi Ekstra: F. Mini Project
Form Pendaftaran Workshop dirancang dengan mensyaratkan kolaborasi (kombinasi fungsi) setidaknya 3 fungsi mandiri, mencakup:
1. **Validasi Karakter Real-time**: Merupakan fitur keamanan dan kenyamanan formulir, yakni menyediakan indikator hitung total jumlah huruf di bagian input Nama Workshop dan secara otomatis melakukan *fallback* sub-string apabila batas kuota lebih dari 50 karakter terlampaui.
2. **Validasi Logika Final Pendaftaran (Submit Event)**: Saat calon peserta mengklik pendaftaran, JavaScript akan mengeksekusi pemeriksaan nama (min. 3 huruf), Regex pendaftaran alamat *e-mail*, dan mendeteksi apakah kotak *dropdown select box* sudah terpilih dengan status *"Sesi Aktif"*, memunculkan respons keberhasilan pendaftaran (*Sukses! Anda terdaftar pada Sesi...*) menggunakan status indikator warna (hijau/merah).
3. **Mekanisme Fitur Reset**: Adanya tombol tambahan `Reset Form` yang tugasnya menangkap *event click*, tidak hanya mengembalikan teks form menjadi usang/kosong, tetapi secara manual ditugaskan untuk menghapus tulisan angka *counter* dan tulisan konfirmasi berhasil atau error agar tampilan bersih seutuhnya.

---

## 6. Penyesuaian Ekstra: G. Eksperimen Mandiri
Untuk membuktikan pendalaman konsep, laporan ini memuat penerapan eksperimental tambahan dari modul:
1. **Fitur Menghapus Data (*Remove Todo List*)**: Mengeksekusi penambahan `<button>` ekstra bewarna merah pada Latihan 6 yang menjalankan fungsi `.remove()`. Dengan begini, tugas bisa disingkirkan dan dihapus sepenuhnya dari alur antarmuka memori DOM tree HTML, dan bukan sekadar dicoret secara gaya CSS.
2. **Validasi Kuota Minimal String Nama (3 Karakter)**: Menginjeksi pengkondisian baru (`nama.length < 3`) di Latihan 5 dan Form Mini Project, mencegah formulir diproses bila panjang ejaan di bawah limit.
3. **Mendeteksi Perubahan (*Event Change*) Pada Elemen Dropdown**: Modifikasi form Mini Project, dipasang listener di atas tipe elemen `select`. Manakala pengguna menavigasi sesi (Pagi, Siang, Malam), akan mencetak teks informasi respons *"Anda memilih..."* seketika itu juga tanpa menunggu form untuk harus disubmit.
4. **Manipulasi Properti Layout (Menampilkan/Menyembunyikan Blok Konten HTML)**: Menyediakan elemen blok paragraf dan tombol interaktif yang memodifikasi klasifikasi nilai gaya CSS `display: none` (kelas `.sembunyikan`), membuktikan jika elemen HTML mampu dibuat muncul dan raib secara ajaib lewat perintah saklar JavaScript.
5. **Keamanan Eksekusi Script dalam Struktur Head (Atribut `defer`)**: Secara eksplisit bereksperimen dengan posisi tag eksternal skrip `<script src="script.js" defer></script>`. Jika ia ditaruh di bagan `<head>` *tanpa* `defer`, pemanggilan `getElementById` akan mengembalikan `null` alias *error*, diakibatkan JavaScript menyala sebelum elemen antarmuka selesai dimuat (Parsing). Penggunaan atribut *defer* membuat JS mematuhi penundaan sementara menunggu seluruh kerangka tulang HTML selesai digambar.

---

## 7. H. Jawaban Pertanyaan Evaluasi Praktikum

**1. Apa yang dimaksud dengan DOM dan apa manfaatnya?**
> Document Object Model (DOM) adalah antarmuka pemrograman terstandarisasi (API) yang merepresentasikan dokumen web (seperti HTML atau XML) ke dalam rupa hierarki objek berupa struktur pohon bersarang (*tree of nodes*). 
> **Manfaatnya:** DOM memberikan "jalan masuk" yang memungkinkan bahasa pemrograman seperti JavaScript untuk terhubung dengan halaman web secara mandiri, menambah, menghapus, atau memanipulasi elemen isi teks serta menyesuaikan bentuk dan rupa (gaya CSS) di halaman secara dinamis di latar belakang tanpa melibatkan kebutuhan memuat ulang atau mem-*refresh* keseluruhan halaman ke *server*.

**2. Apa perbedaan getElementById(), querySelector(), dan querySelectorAll()?**
> - **`getElementById()`**: Merupakan metode pencarian elemen spesifik yang paling lawas, paling cepat (performa tinggi), dirancang eksklusif hanya untuk memanggil 1 (satu) objek secara tunggal dengan mengidentifikasi kecocokan atribut nama `id` unik miliknya.
> - **`querySelector()`**: Sebuah metode pemilih (*selector*) modern yang sangat fleksibel karena menerima semua kaidah aturan format penamaan penyeleksi CSS (bisa berdasarkan titik kelas `.kelas-ini`, pagar tagar `#id-ini`, format tag penamaan HTML `p`, atau hierarki majemuk `div > ul > li`). Fungsi ini hanya mencari dari bagian teratas dan akan mengembalikan objek pada temuan hasil pencocokan pertama saja.
> - **`querySelectorAll()`**: Bekerja dengan menggunakan format pemilih fleksibel CSS yang persis sama, dengan perbedaan fungsi ini tidak berhenti di temuan pertama; ia menelusuri seluruh *node tree* dari atas hingga terbawah, menyeleksi seluruh kecocokan tanpa terkecuali, dan mengembalikan kumpulan hasilnya dalam format senarai/koleksi larik bernama `NodeList`.

**3. Apa fungsi addEventListener() dan sebutkan tiga contoh event?**
> `addEventListener()` adalah fungsi (metode) bawaan yang ditugaskan sebagai "pendengar / mata-mata pemantau". Fungsi ini direkatkan di atas satu elemen DOM, sehingga mesin JavaScript akan senantiasa *stand by* (bersiaga) menanti jenis sinyal kejadian fisik tertentu (dari input manusia atau respon sistem) menyentuh elemen tersebut, barulah ia akan menembakkan instruksi dan mengeksekusi sekumpulan prosedur kode aksi balik.
> **Tiga Contoh Sinyal *Event*:**
> 1. `click` (terpicu saat pengguna melakukan klik kiri *mouse* pada elemen seperti tombol atau *link*).
> 2. `submit` (terpicu secara eksklusif pada lingkup `<form>` manakala diaktifkan saat mengirimkan rincian inputnya).
> 3. `input` atau `change` (terpicu apabila kotak entri isian teks diketik/dipotong nilainya atau saat mengganti nilai *dropdown select*).

**4. Mengapa event.preventDefault() digunakan pada event submit form?**
> Karena tag struktural HTML (terkhususnya komponen form pendaftaran) memiliki karakteristik perilaku genetik bawaan otomatis. Bila form ini disubmit, ia akan seketika itu mencoba mem-POST instruksi jaringan (*network*) ke sistem server tujuan dan memaksa peramban (browser) memuat ulang seluruh kanvas halaman web. Penggunaan `event.preventDefault()` disisipkan untuk memutus perilaku muat-ulang ini, mengizinkan mesin lokal milik *Vanilla JavaScript* mengambil alih hak prerogatif untuk menyaring/mengevaluasi dan memverifikasi kesehatan validasi format formulir data (*Email Format/String Check*) terlebih dahulu secara tenang sebelum proses apapun berjalan lebih jauh.

**5. Apa perbedaan textContent dan innerHTML dari sisi penggunaan dan keamanan?**
> - **`textContent`**: Berfungsi membaca / melempar output dalam status *plain text* (teks ASCII murni mentah-mentah) dan menolak mengenali sisipan format kerangka HTML tambahan. Dari segi keamanan tingkat tinggi, metode ini kebal mutlak terhadap resiko celah injeksi kode serang jahat antar-situs web tipe *XSS (Cross-Site Scripting)*.
> - **`innerHTML`**: Berfungsi merobohkan dan mengubah total bangunan *markup* yang berada di sisi dalam elemen, membaca kembali kode sisipan seperti teks bercetak miring atau tag warna warni HTML baru untuk dapat ter-*render* oleh mesin penampil. Sangat berisiko secara celah keamanan apabila digabungkan bersamaan dengan sumber masuk kolom entri data sembarang pangguna eksternal yang tidak dibersihkan/divalidasi (*sanitize*) lebih dulu.

**6. Bagaimana classList.toggle() membantu mengubah tampilan elemen?**
> Properti sakti DOM ini merupakan instrumen perampingan baris kode yang memangkas kebutuhan untuk merancang struktur percabangan logika rumit seperti `if/else`. 
> Ia bekerja dengan paradigma sakelar sentuh ganda (*flip/flop*); apabila mesin mengecek kelas nama tata letak (*class css*) tersebut belum ada dan belum menempel di dalam elemen, program akan *mengaktifkan* / menambahkannya (*add*). Di detik yang lain bila dieksekusi lagi dan kelasnya telah terpasang, mesin *mencopot* / mendelegasikannya keluar (*remove*). Sederhana, dinamis, dan sangat efisien.

**7. Sebutkan minimal tiga skenario pengujian validasi form.**
> 1) Skenario Ekstrem - Semua kolom input/pilihan sengaja dibiarkan tidak terisi (kosong sama sekali) kemudian tombol simpan ditekan, ini untuk memastikan *form* akan tertahan dan respons pesan error "Nama Wajib Diisi" keluar dengan baik.
> 2) Skenario Uji Format Batas - Menginisiasi pengetikan pada usia menggunakan format angka ekstrem seperti (-50) tahun atau di bawah 17 tahun, serta mengetik kolom form *email* sembarangan (misalnya: "fachruddin2026.gmail") tanpa ada partikel spesial "@", untuk menilai kecerdasan filter dan reguler ekspresi (regex).
> 3) Skenario Kelulusan - Menguji form yang sepenuhnya diisi sesuai prasyarat. Form wajib melaporkan konfirmasi lolos validasi warna pesan hijau (*Sukses*), lantas kolom-kolom input wajib langsung secara mandiri ter-*reset* membersihkan semua string jejak teks masukkannya sebagai indikasi pembersihan sukses untuk entri selanjutnya.
