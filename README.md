# Lab5web

# 1. Operasi dasar aritmatika

<img width="1920" height="1080" alt="Screenshot (112)" src="https://github.com/user-attachments/assets/1b428c62-b46d-4053-8d87-1ad0e077a12e" />


ini adalah contoh dari operasi dasar aritmaika pada javascript

fungsi dari <script language="javascript"> yaitu untuk memberitahu bahwa konten didalamnya adalah javascript

onclick="test(9,4)"Event HandlerAtribut ini adalah event yang dipicu saat tombol diklik. Ia memanggil fungsi test dan memberikan nilai 9 sebagai val1 dan 4 sebagai val2.

# 2. Pembuatan Form Input dan Form Button

<img width="1920" height="1080" alt="Screenshot (113)" src="https://github.com/user-attachments/assets/376b4698-4fa7-4c2e-a10d-ff8a617b6146" />


Fungsi utama dari elemen Input adalah untuk mengumpulkan data dari penggunaseperti Pengambilan Data: Menyediakan kotak teks, checkbox, tombol radio, atau area lain di mana pengguna dapat memasukkan atau memilih informasi.
<input type="text">, <input type="email">



<img width="1920" height="1080" alt="Screenshot (114)" src="https://github.com/user-attachments/assets/b62ecd27-ccfc-4873-a9f1-c0bbf339e1b1" />


Fungsi utama dari Button adalah untuk memicu suatu tindakan atau peristiwa  Digunakan untuk menjalankan fungsi JavaScript tertentu di sisi klien (client-side) saat diklik. (event).Tombol ini dirancang untuk bekerja secara langsung 

<button type="button"> atau <input type="button">


# 3. menggunakan checkbox dengan perhitungan otomatis dan melakukan validasi pada isian form

<img width="1920" height="1080" alt="Screenshot (116)" src="https://github.com/user-attachments/assets/1d7bd706-af50-4df2-a337-7db8b103731d" />

<img width="1850" height="1020" alt="image" src="https://github.com/user-attachments/assets/e4cde362-302e-4e6c-8a60-63fabf3ea301" />

<!DOCTYPE html>
<html>
<head>
  <title>Daftar Menu</title>
  <script>
    // Fungsi untuk menghitung total harga
    function hitungTotal() {
      let ayamGeprek = document.getElementById("menu1");
      let nasiGoreng = document.getElementById("menu2");
      let mieAyam = document.getElementById("menu3");

      let total = 0;

      if (ayamGeprek.checked) total += 10000;
      if (nasiGoreng.checked) total += 15000;
      if (mieAyam.checked) total += 12000;

      document.getElementById("total").value = total;
      document.getElementById("errorMsg").innerHTML = "";
    }

    // Fungsi validasi sebelum form dikirim
    function validasiForm() {
      let ayamGeprek = document.getElementById("menu1").checked;
      let nasiGoreng = document.getElementById("menu2").checked;
      let mieAyam = document.getElementById("menu3").checked;

      // Jika tidak ada menu yang dipilih
      if (!ayamGeprek && !nasiGoreng && !mieAyam) {
        document.getElementById("errorMsg").innerHTML =
          "Silakan pilih minimal satu menu sebelum memproses pesanan.";
        return false;
      }

      // Jika total kosong (misalnya user hapus manual lewat inspect element)
      let total = document.getElementById("total").value;
      if (total === "" || total == 0) {
        document.getElementById("errorMsg").innerHTML =
          "Total tidak boleh kosong. Silakan pilih menu terlebih dahulu.";
        return false;
      }

      document.getElementById("errorMsg").innerHTML = "";
      alert("Pesanan berhasil diproses!\nTotal Bayar: Rp. " + total);
      return true;
    }

    // Cegah pengguna mengetik manual di kolom total
    function cegahEditTotal(event) {
      event.preventDefault();
      return false;
    }
    </script>
</head>
<body>
          <h2>Daftar Menu Makanan</h2>

    <form onsubmit="return validasiForm()">
    <input type="checkbox" id="menu1" onclick="hitungTotal()"> Ayam Geprek Rp. 10.000<br>
    <input type="checkbox" id="menu2" onclick="hitungTotal()"> Nasi Goreng Rp. 15.000<br>
    <input type="checkbox" id="menu3" onclick="hitungTotal()"> Mie Ayam Rp. 12.000<br>
    <hr>

    Total Bayar: Rp. 
    <input 
      type="text" 
      id="total" 
      readonly 
      onkeydown="return cegahEditTotal(event)" 
      onpaste="return false"
      style="width:100px;"
    ><br><br>

    <span id="errorMsg" style="color:red; font-weight:bold;"></span><br>
    <input type="submit" value="Proses Pesanan">
  </form>
</body>
</html>




1. Fungsi hitungTotal()

Dipanggil setiap kali checkbox diubah (klik on/off).

Menjumlahkan harga menu yang dicentang.

Menampilkan hasil di kolom total.

Menghapus pesan error jika pengguna sudah mulai memilih menu.

2. Fungsi validasiForm()

Dijalankan saat tombol submit ditekan.

Mengecek apakah ada menu yang dipilih.

Mengecek apakah kolom total berisi nilai (tidak kosong).

Jika ada kesalahan, form tidak dikirim (return false), dan pesan muncul di <span id="errorMsg">.

Jika valid, muncul alert berisi total pembayaran.


3. Validasi Pesan di Halaman

Semua pesan kesalahan ditampilkan dalam teks berwarna merah di bawah kolom total.

Tidak menggunakan alert() kecuali saat pesanan berhasil.

