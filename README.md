# Refleksi Tutorial 6

<details open>
<summary>Commit 1 Reflection Notes</summary>

Menurut saya pemisahan `handle_connection` dari `main` itu penting karena bikin tugas masing-masing fungsi jadi jelas. `main` sekarang cuma fokus nerima koneksi baru, sedangkan parsing request dipindah ke tempat yang lebih cocok. Waktu saya lihat isi request pakai `BufReader`, saya jadi lebih paham kalau browser ternyata ngirim banyak header, bukan cuma path. Bagian `take_while(|line| !line.is_empty())` juga masuk akal karena HTTP request header memang berhenti di baris kosong. Dari sini saya belajar kalau baca request mentah dulu itu membantu buat ngerti alur sebelum lanjut bikin response. Jadi meskipun server ini belum mengembalikan HTML, tahap ini penting buat ngebuktiin kalau koneksi dan parsing request-nya sudah jalan.

</details>
