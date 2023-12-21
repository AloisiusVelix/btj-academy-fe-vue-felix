# Aplikasi Todo Sederhana

Ini adalah Aplikasi Todo berbasis Vue.js yang memungkinkan pengguna untuk mengelola tugas mereka dengan prioritas yang berbeda. Aplikasi ini menyediakan antarmuka yang ramah pengguna untuk menambahkan tugas baru, menandai mereka sebagai selesai, dan menghapus tugas.

## Fitur

-   **Tampilan Jumlah Tugas:** Aplikasi ini menampilkan jumlah tugas berdasarkan prioritasnya (Menunggu, Prioritas Rendah, Prioritas Menengah, Prioritas Tinggi).
    
-   **Tambah Tugas Baru:** Pengguna dapat menambahkan tugas baru dengan memasukkan nama tugas dan memilih prioritasnya dari menu dropdown. Dengan mengklik tombol "Simpan", tugas ditambahkan ke daftar "TODO".
    
-   **Daftar Tugas:** Aplikasi ini menjaga daftar tugas yang dikategorikan menjadi "TODO" dan "SELESAI". Tugas dalam daftar "TODO" dapat ditandai sebagai selesai atau dihapus.
    
-   **Indikator Prioritas:** Setiap tugas dalam daftar direpresentasikan secara visual dengan indikator berwarna berdasarkan prioritasnya (merah untuk Tinggi, kuning untuk Menengah, dan biru untuk Rendah).
    
-   **Aksi pada Tugas:** Pengguna dapat menghapus tugas atau menandainya sebagai selesai. Tugas yang sudah selesai dipindahkan ke daftar "SELESAI".
    

## Cara Penggunaan

1.  **Lihat Jumlah Tugas:**
    
    -   Jumlah tugas dengan prioritas yang berbeda ditampilkan di bagian atas aplikasi.
2.  **Tambah Tugas Baru:**
    
    -   Isi nama tugas dan pilih prioritasnya dari dropdown.
    -   Klik tombol "Simpan" untuk menambahkan tugas ke daftar "TODO".
3.  **Kelola Tugas:**
    
    -   Di daftar "TODO", setiap tugas ditampilkan dengan nama, prioritas, dan indikator berwarna.
    -   Gunakan tombol "Hapus" untuk menghapus tugas.
    -   Gunakan tombol "Selesai" untuk menandai tugas sebagai selesai.
4.  **Lihat Tugas yang Telah Selesai:**
    
    -   Daftar "SELESAI" menampilkan tugas yang telah ditandai sebagai selesai.

## Struktur Proyek

-   **Template:** Template Vue.js terstruktur dengan bagian untuk jumlah tugas, formulir input, dan daftar tugas.
-   **Script:** Bagian script berisi data, properti terkomputasi, dan metode untuk mengelola fungsionalitas aplikasi.
