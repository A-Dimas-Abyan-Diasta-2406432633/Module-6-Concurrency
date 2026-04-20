# Refleksi Tutorial 6

<details open>
<summary>Commit 1 Reflection Notes</summary>

Menurut saya pemisahan `handle_connection` dari `main` itu penting karena bikin tugas masing-masing fungsi jadi jelas. `main` sekarang cuma fokus nerima koneksi baru, sedangkan parsing request dipindah ke tempat yang lebih cocok. Waktu saya lihat isi request pakai `BufReader`, saya jadi lebih paham kalau browser ternyata ngirim banyak header, bukan cuma path. Bagian `take_while(|line| !line.is_empty())` juga masuk akal karena HTTP request header memang berhenti di baris kosong. Dari sini saya belajar kalau baca request mentah dulu itu membantu buat ngerti alur sebelum lanjut bikin response. Jadi meskipun server ini belum mengembalikan HTML, tahap ini penting buat ngebuktiin kalau koneksi dan parsing request-nya sudah jalan.

</details>

<details>
<summary>Commit 2 Reflection Notes</summary>

Di tahap ini server akhirnya mengirim response yang benar ke browser, jadi hasilnya tidak lagi kosong seperti sebelumnya. Saya baru sadar kalau browser butuh format HTTP response yang rapi, terutama status line, header `Content-Length`, lalu baru isi HTML-nya. Bagian `fs::read_to_string("hello.html")` bikin kontennya lebih enak diatur karena HTML dipisah dari kode Rust. Menurut saya ini lebih bersih dibanding nulis seluruh HTML langsung di string panjang di dalam fungsi. Dari sini saya juga paham kenapa panjang konten harus dihitung dulu, karena browser perlu tahu kapan response selesai dibaca. Intinya, milestone ini menunjukkan bahwa server bukan cuma menerima request, tapi juga sudah bisa mengembalikan halaman HTML sederhana dengan format response yang valid.

![Commit 2 Demo](assets/images/commit2-demo.gif)

</details>
