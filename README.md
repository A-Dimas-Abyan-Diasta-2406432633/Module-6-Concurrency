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

<details>
<summary>Commit 3 Reflection Notes</summary>

Di commit ini saya mulai validasi request line supaya server tidak selalu mengirim halaman yang sama untuk semua path. Sekarang saya ambil baris pertama request saja, lalu saya cocokkan apakah path yang diminta itu `/` atau bukan. Kalau cocok, server balikin `hello.html`, dan kalau tidak, server balikin `404.html` dengan status `404 NOT FOUND`. Menurut saya refactor ke bentuk `let (status_line, filename) = ...` itu penting karena logika pemilihan response jadi lebih ringkas dan tidak bikin duplikasi saat baca file lalu menyusun response HTTP. Sebelumnya alurnya terasa terlalu kaku karena semua request diperlakukan sama, padahal semestinya server bisa membedakan halaman valid dan halaman yang tidak ada. Dari milestone ini saya jadi lebih paham bahwa pemisahan antara penentuan response dan proses menulis response ke stream bikin kode lebih gampang dibaca dan lebih enak dikembangkan ke tahap berikutnya.

Demo tampilan commit 3:

![Commit 3 Demo](assets/images/commit3-demo.gif)

</details>
