# WEEK 2 WORKSHOP
Week 2 ini memiliki beberapa poin materi
    
        -- Http Call
        -- State Managemnt Bloc
        -- Get_storage
        -- Object Model

---

## HTTP CALL

Http call merupakan cara komunikasi anatara aplikasi si user dengan server dengan bantuan API yang disediakan oleh BE.

Http call memiliputi 4 jenis cara, yaitu **get, post , put, dan del**. Setiap cara tersebut bisa saja memiliki data yang harus dikirim dari sever atau data  diterima dari server. Hal tersebut bisa dilihat dari dokumentasi yang diberikan oleh BE, biasanya mereka pakai postman

Contoh Http call: 

```
var _baseUrl = "https://tweet-api.up.railway.app/api";
var _client = http.Client();
var uri = Uri.parse("$_baseUrl/auth/login");

    try {
      var response = await _client.post(uri,
          headers: {"content-type": "application/json"},
          body: json.encode({
            'email': email,
            'password': password,
          }));

      return response.statusCode == 200 ? true : false

    } catch (e) {
      throw (Exception("Eror at Login));
    }
```

_baseUrl sebagai alamat base url server yang diberikan BE. uri sebagai url rute menuju server. Pada proses ini melakukan sebuah proses login

Kita masukan proses http call dalam try catch agar setiap eror pada blok try dapat ditangkap oleh catch dan di handel sehingga aplikasi tidak crash.

Kode di dalam blok try akan dieksekusi apabila terdapat suatu eror akan dimasukan dalam blok catch. Referensi: [try-cath Dokumentasi](https://www.tutorialkart.com/dart/dart-try-catch/)

Kita masuk ke dalam variabel response dimana http call terjadi. Perlu di ingat proses komunikasi menuju server tidak memiliki waktu eksekusi yang sama. oleh karena itu, proses komunikasi ini berlangsung secara asikronus dengan harapan flutter tau kita menunggu jawaban dari server sebelum menjalankan proses lainnya

Proses komunikasi ke server setidaknya membutuhkan 3 macam parameter, yaitu **uri, headers, body**

Uri => sebagai url rute menuju suatu servis pada server

headers => Semacam kop surat untuk komunikasi server. Yang paling umum berisikan bearer token (Keperluan header bisa didiskusikan dengan BE)

body => berisikan sebuah data yang dikirim dengan bentuk json map. 

json ke dart menggunakan json.decode. Sedangkan, dart ke json menggunakan json.encode. Perlu di inget import dart:convert.

Proses http call terdapat sebuah response code untuk menyatakan balasan dari server. Response code berhasil ditandai dengan angka 2xx. Response code ini bisa dilihat dokumentasi postman

---

## State Management Bloc

Pembuaatan aplikasi flutter usahakan desain dengan logic dipisahkan, lalu bagaimana menghubungkan antara logic dan desain?. Jawabannya dengan bantuan State management.

State management adalah sebuah cara untuk mengatur data / state kita bekerja, bisa juga untuk memisahkan antara logic dan view, dimana logic tersebut juga bisa reusable. Referensi : [State Management Flutter](https://caraguna.com/pengenalan-state-management-flutter/)

Bloc merupakan state management yang memiliki basis event dan state untuk melakukan indetifikasi perubahan dalam aplikasi. **Event** bisa dibilang peristiwa interaksi user dengan aplikasi, contoh user melakukan login, user menekan tombol bayar, dll. **State** adalah kondisi aplikasi saat menerima suatu inputan atau data.


![Interaksi bloc](https://miro.medium.com/v2/resize:fit:720/format:webp/0*EG9GW70kfdesSPRZ.png)

Saat generate file bloc akan memiliki 3 file yang memiliki fungsi sendiri, yaitu:

**1. _file_ _bloc.dart** .<br>
      file_bloc.dart merupakan file yang berisikan bagaimana kita mengatur antara state dan hasil response data


**2. _file_ _state.dart** .<br>
      file_state.dart merupakan file berisikan state/kondisi aplikasi sebagai bentuk hasil response suatu data


**3. _file_ _event.dart** .<br>
      file_event.dart merupakan file berisikan event yang didasarkan interaksi user kepada aplikasi














