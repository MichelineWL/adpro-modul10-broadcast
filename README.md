## Refleksi Modul 10 - Broadcast

### Nama : Micheline Wijaya Limbergh
### NPM : 2306207013

![image](https://github.com/user-attachments/assets/31f17db3-2cf7-4930-a8c2-7228c1df771b)
Pada ilustrasi tersebut, terdapat satu server dan tiga klien yang berjalan secara bersamaan. Setiap klien langsung tersambung ke server saat dijalankan. Ketika salah satu klien mengirim pesan, pesan tersebut akan diterima terlebih dahulu oleh server. Setelah itu, server akan membagikan pesan tersebut ke seluruh klien yang sedang terhubung, termasuk klien pengirimnya. Proses ini memungkinkan seluruh klien untuk saling melihat pesan secara langsung tanpa jeda. Pola komunikasi ini dimungkinkan karena server menyebarkan pesan dengan format tertentu, misalnya diawali dengan "From server:", lalu diikuti isi pesan, agar semua klien dapat menampilkannya secara konsisten.


Mengganti port :
![image](https://github.com/user-attachments/assets/f0dc14d8-b425-4548-949d-5eb3819af18e)
Agar koneksi antara server dan client berhasil, nomor port yang digunakan pada kedua sisi harus sama. Jika ingin mengubah port komunikasi, maka penyesuaian perlu dilakukan baik pada file `client.rs` maupun `server.rs`. Di dalam `client.rs`, bagian `ClientBuilder::from_uri(...)` harus diubah agar mengarah ke alamat dan port tujuan yang baru. Sementara itu, di `server.rs`, bagian `TcpListener::bind(...)` juga perlu disesuaikan agar server dapat menerima koneksi pada port yang sama. Komunikasi yang terjadi menggunakan protokol WebSocket, sebagaimana terlihat dari penggunaan awalan `ws://` di URI client dan pemanfaatan `ServerBuilder` yang membungkus `TcpListener` pada sisi server. Jika port yang digunakan telah sinkron di kedua sisi, maka proses koneksi akan berhasil dan komunikasi dapat berlangsung dengan lancar. Sebaliknya, jika hanya salah satu sisi yang mengalami perubahan port tanpa penyesuaian pada sisi lain, maka koneksi tidak dapat terbentuk karena ketidakcocokan alamat tujuan.

