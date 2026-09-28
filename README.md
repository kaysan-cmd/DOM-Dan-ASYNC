# DOM-Dan-ASYNC

-DOCUMENT OBJECT MODEL (DOM)

Penjelasan
DOM (Document Object Model) adalah antarmuka pemrograman (API) standar untuk dokumen HTML dan XML. DOM merepresentasikan struktur halaman web sebagai pohon objek (tree structure), di mana setiap elemen HTML menjadi node/objek yang dapat diakses dan dimanipulasi menggunakan JavaScript.

Penjelasan
Saat browser memuat halaman web, HTML diubah menjadi struktur DOM di memori. Dengan DOM, JavaScript dapat:
-Mengubah isi teks atau struktur elemen HTML secara dinamis.
-Mengubah gaya (CSS style) elemen.
-Menambah, menghapus, atau memindahkan elemen.
-Merespons interaksi pengguna seperti klik, ketikan keyboard, atau pergerakan kursor (Event Handling).

Contoh
HTML:

<h1 id="judul">Teks Awal</h1>
<button id="btnUbah">Ubah Judul</button>

JavaScript:
-Mengambil elemen dari DOM berdasarkan ID
const judul = document.getElementById('judul');
const tombol = document.getElementById('btnUbah');

-Menambahkan event listener saat tombol diklik
tombol.addEventListener('click', () => {
-Memanipulasi teks dan gaya CSS elemen
judul.textContent = 'Judul Berhasil Diubah!';
judul.style.color = 'blue';
});

-ASYNCHRONOUS (ASYNC)

Pengertian
Asynchronous (Async) adalah teknik pemrograman yang memungkinkan suatu proses dijalankan di latar belakang tanpa menghentikan (non-blocking) eksekusi baris kode berikutnya.

Penjelasan
Secara default, JavaScript berjalan secara Synchronous (berurutan dari atas ke bawah). Jika ada tugas yang memakan waktu lama (seperti mengambil data dari server), kode di bawahnya harus menunggu sampai proses tersebut selesai.

Dengan teknik Asynchronous, JavaScript mengirim permintaan data di latar belakang dan langsung melanjutkan eksekusi kode berikutnya. Ketika data siap, JavaScript baru memproses hasil tersebut. Fitur Async modern pada JavaScript umumnya dikelola menggunakan Promise dan sintaks async/await.

Contoh:
JavaScript (menggunakan async/await dan fetch API):

async function ambilDataPengguna() {
try {
console.log("1. Memulai proses ambil data...");

    // 'await' menunggu proses fetch tanpa menghentikan program di luar fungsi
    const response = await fetch('https://jsonplaceholder.typicode.com/users/1');
    const data = await response.json();

    console.log("3. Data berhasil diterima:", data.name);

} catch (error) {
console.error("Terjadi kesalahan:", error);
}
}

-Memanggil fungsi async
ambilDataPengguna();

-Baris ini dijalankan LEBIH DULU sebelum fetch selesai
console.log("2. Kode lain tetap berjalan tanpa terhambat!");

Output di Konsol:
-Memulai proses ambil data...
-Kode lain tetap berjalan tanpa terhambat!
-Data berhasil diterima: Leanne Graham
