# Praktikum 11

Project Modul 11 - Manajemen State dengan GetX

📖 Deskripsi

Project ini adalah modul lanjutan yang berfokus pada Manajemen State. Anda akan membuat ulang aplikasi Tasbih Digital dari Modul 9, namun kali ini mengganti StatefulWidget dan setState() dengan state management library populer: GetX.

Fokus utamanya adalah memisahkan logic (logika bisnis) dari view (tampilan) menggunakan Controller, dan memperbarui UI secara otomatis (reaktif) menggunakan variabel .obs dan widget Obx.

🎯 Tujuan Utama Project

Memahami GetX: Mengerti konsep dasar state management reaktif menggunakan GetX.

Membandingkan Pendekatan: Membedakan cara kerja setState() (Modul 9) dengan pendekatan GetX yang lebih efisien (tanpa setState()).

Menerapkan Controller: Mampu membuat GetxController untuk menyimpan semua logic dan state (variabel).

Variabel Reaktif: Mampu menggunakan variabel reaktif (menambahkan .obs) yang secara otomatis akan memicu pembaruan UI.

Widget Reaktif: Menggunakan widget Obx untuk membungkus UI yang perlu diperbarui saat state berubah.

✅ Daftar Tugas (To-Do List)

Berikut adalah hal-hal yang harus Anda kerjakan untuk me-refactor aplikasi Tasbih Digital menggunakan GetX:

Buat Project Baru:

[ ] Buat "New Flutter Project" dengan nama getx_app.

Tambahkan Dependency (Penting!):

[ ] Buka file pubspec.yaml.

[ ] Tambahkan package getx di bawah dependencies:.

[ ] Jalankan flutter pub get di terminal.

Buat Struktur Folder (Best Practice):

[ ] Di dalam lib/, buat 3 folder: model, view, dan viewmodel.

viewmodel akan berisi Controller Anda.

view akan berisi file UI (halaman) Anda.

Buat Controller (viewmodel/tasbih_controller.dart):

[ ] Buat class baru, misal TasbihController, yang extends GetxController.

[ ] Definisikan Variabel Reaktif (State):

var counter = 0.obs; (Gunakan .obs untuk membuatnya reaktif).

var progress = 0.0.obs; (Untuk progress bar).

[ ] Buat Method (Logic):

void incrementCounter():

counter++;

Hitung progress.value (misal: counter.value % 33 / 33.0).

(Catatan: Anda tidak perlu memanggil setState()).

void resetCounter():

counter.value = 0;

progress.value = 0.0;

Kode Tampilan (view/home_page.dart):

[ ] Buat StatelessWidget untuk halaman Anda (Anda tidak perlu StatefulWidget lagi).

[ ] Inisialisasi Controller:

Di dalam method build, inisialisasi controller Anda:
final TasbihController c = Get.put(TasbihController());

[ ] Gunakan Obx pada UI yang Berubah:

Bungkus Text yang menampilkan counter dengan Obx:
Obx(() => Text('${c.counter.value}'))

Bungkus SimpleCircularProgressBar dengan Obx dan gunakan c.progress.value.

[ ] Hubungkan Aksi (Action):

onTap pada InkWell (progress bar) diisi: () => c.incrementCounter().

onPressed pada FloatingActionButton diisi: () => c.resetCounter().

Konfigurasi main.dart:

[ ] Ubah MaterialApp menjadi GetMaterialApp.

[ ] Arahkan home ke halaman HomePage (dari folder view) Anda.
