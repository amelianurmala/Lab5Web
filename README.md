# Lab5Web
# Praktikum 5: Javascript

## *Nama: Ameliaa Nurmala Dewi*
## *NIM: 312410199*
## *Kelas: TI.24.A2*


## 1. Membuat Struktur Dasar HTML

<img width="665" height="708" alt="Screenshot (838)" src="https://github.com/user-attachments/assets/753f69e6-ca11-46f7-a69d-0807bc6c3a71" />

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Form Pemesanan Barang</title>
</head>
<body>
    <h1>Form Pemesanan Barang</h1>

    <form name="formPesan">
        <label>Nama Pembeli:</label><br>
        <input type="text" id="nama"><br><br>

        <label>Alamat:</label><br>
        <textarea id="alamat" rows="3"></textarea><br><br>

        <label>Nomor HP:</label><br>
        <input type="text" id="hp"><br><br>

        <label>Pilih Barang:</label><br>
        <select id="barang">
            <option value="">-- Pilih Barang --</option>
            <option value="Makeup">Makeup</option>
            <option value="Skincare">Skincare</option>
            <option value="Parfum">Parfum</option>
        </select><br><br>

        <input type="submit" value="Kirim Pesanan">
    </form>
</body>
</html>

```

### Penjelasan

Pada tahap pertama, saya membuat struktur dasar HTML berisi form sederhana untuk **pemesanan barang**.  
Form ini berisi kolom:
- Nama Pembeli  
- Alamat  
- Nomor HP  
- Pilihan Barang  

Belum ada CSS dan JavaScript, jadi tampilannya masih polos seperti gambar di atas.  
Namun fungsinya sudah ada, yaitu menampilkan form input dasar yang nantinya akan divalidasi menggunakan JavaScript.

---

## 2. Menambahkan JavaScript Validasi Form

<img width="661" height="706" alt="Screenshot (837)" src="https://github.com/user-attachments/assets/693a1e7d-070a-45f2-80cc-dd569e986760" />

```
<form name="formPesan" onsubmit="return validasiPesanan()">
    ...
</form>

<script>
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

        alert("Pesanan berhasil dikirim!");
        return true;
    }
</script>
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

## 3. Menambahkan CSS agar Tampilan Menarik

<img width="665" height="704" alt="Screenshot (822)" src="https://github.com/user-attachments/assets/52c6c2b3-d2d0-4cfd-9744-54115706b6aa" />

```
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


## 4. Hasil Akhir Validasi Form Berhasil Dikirim

<img width="662" height="706" alt="Screenshot (823)" src="https://github.com/user-attachments/assets/0e57fba2-07c7-46c0-b2bf-dc7d00852982" />


### Penjelasan

Pada tahap terakhir ini, setelah semua kolom diisi dengan benar, form akan menampilkan **pesan pop-up alert** bertuliskan:

> "Pesanan berhasil dikirim!"

Pesan ini muncul karena semua data yang dimasukkan sudah sesuai dengan kondisi yang ada di dalam fungsi `validasiPesanan()`.

Berikut alurnya:
1. Pengguna menekan tombol **Kirim Pesanan**.  
2. JavaScript memeriksa semua kolom input satu per satu:
   - Jika ada kolom kosong → muncul peringatan error.  
   - Jika semua kolom benar → menjalankan `alert("Pesanan berhasil dikirim!");`  
3. Pesan alert ini menandakan bahwa data **siap dikirim atau diproses**.

Tampilan akhirnya terlihat menarik karena sudah dikombinasikan antara:
- **HTML** sebagai struktur form,  
- **CSS** untuk mempercantik tampilan,  
- dan **JavaScript** untuk logika validasinya.

---

## Kesimpulan 

Dari keseluruhan hasil praktikum ini, saya memahami bahwa:
- **HTML** digunakan untuk membuat struktur form pemesanan barang.  
- **JavaScript** digunakan untuk memvalidasi data agar tidak ada kolom yang kosong atau salah input.  
- **CSS** digunakan agar tampilan form terlihat menarik dan profesional.  

Hasil akhirnya menampilkan pop-up alert “Pesanan berhasil dikirim!” sebagai tanda bahwa validasi berjalan dengan baik dan form sudah siap dikirim ke sistem.




