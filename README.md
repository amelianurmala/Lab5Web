# Lab5Web
# Praktikum 5: Javascript

## *Nama: Ameliaa Nurmala Dewi*
## *NIM: 312410199*
## *Kelas: TI.24.A2*


## 1. Tampilan Awal (Alert Selamat Datang)

<img width="663" height="710" alt="Screenshot (844)" src="https://github.com/user-attachments/assets/f9c3393c-75f1-4028-939b-421d2b4f9adf" />

```
alert("Selamat datang di Form Pemesanan Barang!");
```

### Penjelasan

- Dialog ini dibuat dengan JavaScript menggunakan fungsi alert("Selamat datang di Form Pemesanan Barang!");
- Biasanya diletakkan di dalam tag <script> di bagian <body> atau di akhir file HTML agar muncul otomatis ketika halaman dimuat.
- Fungsinya untuk menyapa pengguna sebelum mereka mulai mengisi form.

---

## 2. Dialog Input Nama (Prompt)

<img width="665" height="712" alt="Screenshot (845)" src="https://github.com/user-attachments/assets/c7a69a86-3977-4ab6-9b07-95111733b35b" />

### Penjelasan

- Ini dibuat menggunakan fungsi prompt("Masukkan nama Anda:");
- User mengetik nama mereka (misalnya “amelia”) lalu menekan tombol Oke.
- Nilai yang dimasukkan disimpan ke dalam variabel JavaScript, misalnya:
```
var nama = prompt("Masukkan nama Anda:");
```
- Data ini kemudian digunakan untuk menampilkan pesan sambutan di halaman.

---

## 3. Halaman Form Setelah Nama Diinput

<img width="663" height="704" alt="Screenshot (849)" src="https://github.com/user-attachments/assets/9f508aaf-ab78-464e-a78b-d814518ab83e" />

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Form Pemesanan Barang</title>
</head>
<body>
    <h1>Form Pemesanan Barang</h1>

    <script>
        // PEMAKAIAN ALERT DAN PROMPT
        alert("Selamat datang di Form Pemesanan Barang!");
        var namaUser = prompt("Masukkan nama Anda:");
        document.write("<h3 style='text-align:center; color:#555;'>Halo " + namaUser + ", silakan isi form di bawah ini untuk melakukan pemesanan.</h3>");
    </script>

    <form name="formPesan" onsubmit="return validasiPesanan()">
        <!-- INPUT DASAR -->
        <label>Nama Pembeli:</label>
        <input type="text" id="nama" placeholder="Masukkan nama lengkap">

        <label>Alamat:</label>
        <textarea id="alamat" rows="3" placeholder="Masukkan alamat lengkap"></textarea>

        <label>Nomor HP:</label>
        <input type="text" id="hp" placeholder="Contoh: 081234567890">

        <label>Pilih Barang:</label>
        <select id="barang" onchange="cekBarang()">
            <option value="">-- Pilih Barang --</option>
            <option value="Makeup">Makeup</option>
            <option value="Skincare">Skincare</option>
            <option value="Parfum">Parfum</option>
        </select>

        <!-- CHECKBOX BARANG TAMBAHAN DENGAN PERHITUNGAN -->
        <label>Pilih Tambahan:</label>
        <label><input type="checkbox" value="20000" onclick="hitungTotal(this)"> Kotak Kado (+Rp20.000)</label><br>
        <label><input type="checkbox" value="10000" onclick="hitungTotal(this)"> Plastik Premium (+Rp10.000)</label><br>
        <label><input type="checkbox" value="5000" onclick="hitungTotal(this)"> Pita Hias (+Rp5.000)</label><br>

        <hr>
        <label>Total Harga Tambahan:</label>
        <input type="text" id="total" class="total" value="0" readonly>

        <hr>
        <input type="submit" value="Kirim Pesanan">
        <input type="button" value="Reset" onclick="resetForm()">
    </form>

    <script>
        // VARIABEL GLOBAL
        var total = 0;

        // OPERASI ARITMATIKA (MENGHITUNG TOTAL)
        function hitungTotal(cb) {
            if (cb.checked) {
                total += parseInt(cb.value);
            } else {
                total -= parseInt(cb.value);
            }
            document.getElementById("total").value = total;
        }

        // SWITCH UNTUK CEK BARANG
        function cekBarang() {
            var barang = document.getElementById("barang").value;
            switch (barang) {
                case "Makeup":
                    alert("Anda memilih Makeup. Harga mulai Rp150.000");
                    break;
                case "Skincare":
                    alert("Anda memilih Skincare. Harga mulai Rp200.000");
                    break;
                case "Parfum":
                    alert("Anda memilih Parfum. Harga mulai Rp250.000");
                    break;
                default:
                    alert("Silakan pilih jenis barang terlebih dahulu!");
            }
        }

        // FUNGSI VALIDASI DENGAN IF..ELSE
        function validasiPesanan() {
            var nama = document.getElementById("nama").value;
            var alamat = document.getElementById("alamat").value;
            var hp = document.getElementById("hp").value;
            var barang = document.getElementById("barang").value;

            if (nama == "") {
                alert("Nama pembeli wajib diisi!");
                return false;
            }
            if (alamat == "") {
                alert("Alamat tidak boleh kosong!");
                return false;
            }
            if (hp == "") {
                alert("Nomor HP wajib diisi!");
                return false;
            } else if (isNaN(hp)) {
                alert("Nomor HP hanya boleh angka!");
                return false;
            }
            if (barang == "") {
                alert("Pilih barang yang ingin dipesan!");
                return false;
            }

            alert("Pesanan atas nama " + nama + " berhasil dikirim!\nTotal tambahan: Rp" + total);
            return true;
        }

        // FUNGSI RESET FORM
        function resetForm() {
            document.getElementById("nama").value = "";
            document.getElementById("alamat").value = "";
            document.getElementById("hp").value = "";
            document.getElementById("barang").value = "";
            document.getElementById("total").value = 0;
            total = 0;
            alert("Form telah direset.");
        }
    </script>
</body>
</html>
```

### Penjelasan 

Setelah nama dimasukkan, halaman menampilkan teks sambutan:

`“Halo amelia, silakan isi form di bawah ini!”`

-Elemen teks ini diubah menggunakan JavaScript:

`document.getElementById("sambutan").innerText = "Halo " + nama + ", silakan isi form di bawah ini!";`

Artinya, bagian <p id="sambutan"></p> di HTML diubah isinya sesuai nama yang dimasukkan pengguna.

Di bawahnya terdapat form pemesanan dengan beberapa field seperti:

- Nama Pembeli
- Alamat
- Nomor HP
- Pilihan Barang
- Tombol Kirim Pesanan

---

## 4. Menambahkan JavaScript Validasi Form

<img width="665" height="708" alt="Screenshot (855)" src="https://github.com/user-attachments/assets/2dc398b8-8763-4c4e-b727-82697ca9bd05" />


```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Form Pemesanan Barang</title>
   <style>
    body {
        font-family: Arial, sans-serif;
        background-color: #f7f7f7;
        padding: 40px;
    }
    h1 {
        text-align: center;
        color: #333;
    }
    form {
        width: 400px;
        margin: auto;
        background: #fff;
        padding: 25px;
        border-radius: 12px;
        box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    label {
        font-weight: bold;
    }
    input, textarea, select {
        width: 100%;
        padding: 8px;
        margin: 6px 0 15px 0;
        border: 1px solid #ccc;
        border-radius: 6px;
    }
    input[type="submit"] {
        background-color: #007bff;
        color: white;
        cursor: pointer;
        transition: 0.3s;
    }
    input[type="submit"]:hover {
        background-color: #0056b3;
    }
</style>

</head>
<body>
    <h1>Form Pemesanan Barang</h1>

    <script>
        // PEMAKAIAN ALERT DAN PROMPT
        alert("Selamat datang di Form Pemesanan Barang!");
        var namaUser = prompt("Masukkan nama Anda:");
        document.write("<h3 style='text-align:center; color:#555;'>Halo " + namaUser + ", silakan isi form di bawah ini untuk melakukan pemesanan.</h3>");
    </script>

    <form name="formPesan" onsubmit="return validasiPesanan()">
        <!-- INPUT DASAR -->
        <label>Nama Pembeli:</label>
        <input type="text" id="nama" placeholder="Masukkan nama lengkap">

        <label>Alamat:</label>
        <textarea id="alamat" rows="3" placeholder="Masukkan alamat lengkap"></textarea>

        <label>Nomor HP:</label>
        <input type="text" id="hp" placeholder="Contoh: 081234567890">

        <label>Pilih Barang:</label>
        <select id="barang" onchange="cekBarang()">
            <option value="">-- Pilih Barang --</option>
            <option value="Makeup">Makeup</option>
            <option value="Skincare">Skincare</option>
            <option value="Parfum">Parfum</option>
        </select>

        <!-- CHECKBOX BARANG TAMBAHAN DENGAN PERHITUNGAN -->
        <label>Pilih Tambahan:</label>
        <label><input type="checkbox" value="20000" onclick="hitungTotal(this)"> Kotak Kado (+Rp20.000)</label><br>
        <label><input type="checkbox" value="10000" onclick="hitungTotal(this)"> Plastik Premium (+Rp10.000)</label><br>
        <label><input type="checkbox" value="5000" onclick="hitungTotal(this)"> Pita Hias (+Rp5.000)</label><br>

        <hr>
        <label>Total Harga Tambahan:</label>
        <input type="text" id="total" class="total" value="0" readonly>

        <hr>
        <input type="submit" value="Kirim Pesanan">
        <input type="button" value="Reset" onclick="resetForm()">
    </form>

    <script>
        // VARIABEL GLOBAL
        var total = 0;

        // OPERASI ARITMATIKA (MENGHITUNG TOTAL)
        function hitungTotal(cb) {
            if (cb.checked) {
                total += parseInt(cb.value);
            } else {
                total -= parseInt(cb.value);
            }
            document.getElementById("total").value = total;
        }

        // SWITCH UNTUK CEK BARANG
        function cekBarang() {
            var barang = document.getElementById("barang").value;
            switch (barang) {
                case "Makeup":
                    alert("Anda memilih Makeup. Harga mulai Rp150.000");
                    break;
                case "Skincare":
                    alert("Anda memilih Skincare. Harga mulai Rp200.000");
                    break;
                case "Parfum":
                    alert("Anda memilih Parfum. Harga mulai Rp250.000");
                    break;
                default:
                    alert("Silakan pilih jenis barang terlebih dahulu!");
            }
        }

        // FUNGSI VALIDASI DENGAN IF..ELSE
        function validasiPesanan() {
            var nama = document.getElementById("nama").value;
            var alamat = document.getElementById("alamat").value;
            var hp = document.getElementById("hp").value;
            var barang = document.getElementById("barang").value;

            if (nama == "") {
                alert("Nama pembeli wajib diisi!");
                return false;
            }
            if (alamat == "") {
                alert("Alamat tidak boleh kosong!");
                return false;
            }
            if (hp == "") {
                alert("Nomor HP wajib diisi!");
                return false;
            } else if (isNaN(hp)) {
                alert("Nomor HP hanya boleh angka!");
                return false;
            }
            if (barang == "") {
                alert("Pilih barang yang ingin dipesan!");
                return false;
            }

            alert("Pesanan atas nama " + nama + " berhasil dikirim!\nTotal tambahan: Rp" + total);
            return true;
        }

        // FUNGSI RESET FORM
        function resetForm() {
            document.getElementById("nama").value = "";
            document.getElementById("alamat").value = "";
            document.getElementById("hp").value = "";
            document.getElementById("barang").value = "";
            document.getElementById("total").value = 0;
            total = 0;
            alert("Form telah direset.");
        }
    </script>
</body>
</html>
```

### Penjelasan

Setelah struktur form selesai, saya menambahkan **JavaScript** dengan fungsi `validasiPesanan()`.  
Tujuannya untuk memeriksa apakah semua kolom sudah diisi dengan benar.

Penjelasan singkat kodenya:
- Mengecek apakah kolom **Nama Pembeli** kosong.  
- Mengecek apakah kolom **Alamat** kosong.  
- Mengecek apakah **Nomor HP** hanya berisi angka (`isNaN`).  
- Mengecek apakah barang sudah dipilih.  
Jika ada yang kosong, maka muncul peringatan `alert()` agar pengguna melengkapi datanya.

Tampilan belum berubah secara visual, tapi fungsinya sudah mulai berjalan sesuai perintah validasi di JavaScript.

---

## 5. Menambahkan CSS agar Tampilan Menarik

<img width="667" height="712" alt="Screenshot (852)" src="https://github.com/user-attachments/assets/b4c39596-24bd-4ed3-8f03-0b40d8d82f8b" />

<img width="663" height="712" alt="Screenshot (853)" src="https://github.com/user-attachments/assets/d097f630-0b1e-4354-a1a8-97f0e190f5b6" />

<img width="663" height="708" alt="Screenshot (854)" src="https://github.com/user-attachments/assets/266688db-70d1-47f5-85ab-11691a4228b4" />


```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Form Pemesanan Barang</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f8bcda;
            padding: 40px;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        form {
            width: 450px;
            margin: auto;
            background: #ec49a3;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
            color: white;
        }
        label {
            font-weight: bold;
        }
        input, textarea, select {
            width: 100%;
            padding: 8px;
            margin: 6px 0 15px 0;
            border: 1px solid #ccc;
            border-radius: 6px;
        }
        input[type="submit"], input[type="button"] {
            background-color: #007bff;
            color: white;
            cursor: pointer;
            border: none;
            padding: 10px;
            transition: 0.3s;
            border-radius: 6px;
        }
        input[type="submit"]:hover, input[type="button"]:hover {
            background-color: #0056b3;
        }
        .total {
            background-color: white;
            color: black;
            padding: 8px;
            border-radius: 6px;
        }
    </style>
</head>
<body>
    <h1>Form Pemesanan Barang</h1>

    <script>
        // PEMAKAIAN ALERT DAN PROMPT
        alert("Selamat datang di Form Pemesanan Barang!");
        var namaUser = prompt("Masukkan nama Anda:");
        document.write("<h3 style='text-align:center; color:#555;'>Halo " + namaUser + ", silakan isi form di bawah ini untuk melakukan pemesanan.</h3>");
    </script>

    <form name="formPesan" onsubmit="return validasiPesanan()">
        <!-- INPUT DASAR -->
        <label>Nama Pembeli:</label>
        <input type="text" id="nama" placeholder="Masukkan nama lengkap">

        <label>Alamat:</label>
        <textarea id="alamat" rows="3" placeholder="Masukkan alamat lengkap"></textarea>

        <label>Nomor HP:</label>
        <input type="text" id="hp" placeholder="Contoh: 081234567890">

        <label>Pilih Barang:</label>
        <select id="barang" onchange="cekBarang()">
            <option value="">-- Pilih Barang --</option>
            <option value="Makeup">Makeup</option>
            <option value="Skincare">Skincare</option>
            <option value="Parfum">Parfum</option>
        </select>

        <!-- CHECKBOX BARANG TAMBAHAN DENGAN PERHITUNGAN -->
        <label>Pilih Tambahan:</label>
        <label><input type="checkbox" value="20000" onclick="hitungTotal(this)"> Kotak Kado (+Rp20.000)</label><br>
        <label><input type="checkbox" value="10000" onclick="hitungTotal(this)"> Plastik Premium (+Rp10.000)</label><br>
        <label><input type="checkbox" value="5000" onclick="hitungTotal(this)"> Pita Hias (+Rp5.000)</label><br>

        <hr>
        <label>Total Harga Tambahan:</label>
        <input type="text" id="total" class="total" value="0" readonly>

        <hr>
        <input type="submit" value="Kirim Pesanan">
        <input type="button" value="Reset" onclick="resetForm()">
    </form>

    <script>
        // VARIABEL GLOBAL
        var total = 0;

        // OPERASI ARITMATIKA (MENGHITUNG TOTAL)
        function hitungTotal(cb) {
            if (cb.checked) {
                total += parseInt(cb.value);
            } else {
                total -= parseInt(cb.value);
            }
            document.getElementById("total").value = total;
        }

        // SWITCH UNTUK CEK BARANG
        function cekBarang() {
            var barang = document.getElementById("barang").value;
            switch (barang) {
                case "Makeup":
                    alert("Anda memilih Makeup. Harga mulai Rp150.000");
                    break;
                case "Skincare":
                    alert("Anda memilih Skincare. Harga mulai Rp200.000");
                    break;
                case "Parfum":
                    alert("Anda memilih Parfum. Harga mulai Rp250.000");
                    break;
                default:
                    alert("Silakan pilih jenis barang terlebih dahulu!");
            }
        }

        // FUNGSI VALIDASI DENGAN IF..ELSE
        function validasiPesanan() {
            var nama = document.getElementById("nama").value;
            var alamat = document.getElementById("alamat").value;
            var hp = document.getElementById("hp").value;
            var barang = document.getElementById("barang").value;

            if (nama == "") {
                alert("Nama pembeli wajib diisi!");
                return false;
            }
            if (alamat == "") {
                alert("Alamat tidak boleh kosong!");
                return false;
            }
            if (hp == "") {
                alert("Nomor HP wajib diisi!");
                return false;
            } else if (isNaN(hp)) {
                alert("Nomor HP hanya boleh angka!");
                return false;
            }
            if (barang == "") {
                alert("Pilih barang yang ingin dipesan!");
                return false;
            }

            alert("Pesanan atas nama " + nama + " berhasil dikirim!\nTotal tambahan: Rp" + total);
            return true;
        }

        // FUNGSI RESET FORM
        function resetForm() {
            document.getElementById("nama").value = "";
            document.getElementById("alamat").value = "";
            document.getElementById("hp").value = "";
            document.getElementById("barang").value = "";
            document.getElementById("total").value = 0;
            total = 0;
            alert("Form telah direset.");
        }
    </script>
</body>
</html>

```

### Penjelasan

Pada tahap ini saya menambahkan **kode CSS** untuk mempercantik tampilan form.  
Saya ubah warna latar belakang menjadi **pink lembut**, memberi efek **bayangan pada form**, dan membuat tombol **Kirim Pesanan** berwarna biru agar menarik perhatian pengguna.

Perubahan yang dilakukan:
- Warna background halaman menjadi `#f5b3c8`.  
- Warna form menjadi `#cc6787` dengan sudut membulat (`border-radius: 12px`).  
- Tombol submit diberi efek hover agar lebih interaktif.  
- Form ditata agar berada di tengah halaman (`margin: auto`).  

Hasil akhirnya seperti gambar di atas — form terlihat lebih modern, rapi, dan mudah dibaca.

---

## Kesimpulan 

Dari keseluruhan hasil praktikum ini, saya memahami bahwa:
- **HTML** digunakan untuk membuat struktur form pemesanan barang.  
- **JavaScript** digunakan untuk memvalidasi data agar tidak ada kolom yang kosong atau salah input.  
- **CSS** digunakan agar tampilan form terlihat menarik dan profesional.  

Hasil akhirnya menampilkan pop-up alert “Pesanan berhasil dikirim!” sebagai tanda bahwa validasi berjalan dengan baik dan form sudah siap dikirim ke sistem.




