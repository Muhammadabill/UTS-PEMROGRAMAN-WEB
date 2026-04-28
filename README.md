# Eksperimen Keamanan Web: Pencegahan SQL Injection pada Sistem Login Admin Berbasis CodeIgniter 4

## Nama : Muhamad Nabil Satriya Suntara
## Nim : 312410365
## Matkul : Pemrograman Web
## Kelas : I241D

## Pendahuluan

Dalam pengembangan website, keamanan sistem merupakan hal yang sangat penting. Salah satu ancaman yang paling sering terjadi adalah SQL Injection (SQLi). Serangan ini terjadi ketika penyerang memasukkan perintah SQL berbahaya melalui form input seperti login, pencarian, atau formulir lainnya. Jika tidak ditangani dengan baik, serangan ini dapat menyebabkan kebocoran data dan akses ilegal ke sistem.

Pada eksperimen ini, saya menganalisis fitur login admin pada project berbasis CodeIgniter 4 untuk melihat bagaimana sistem mencegah serangan SQL Injection. Framework CodeIgniter 4 menyediakan Query Builder yang membantu mengamankan proses query database agar input pengguna tidak langsung diproses sebagai perintah SQL.

---

## Skenario Eksperimen

Eksperimen dilakukan pada form login admin dengan input email dan password. Sistem menggunakan proses pencarian data pengguna berdasarkan email yang dimasukkan saat login.

Pada proses ini, saya mengamati apakah sistem menggunakan query manual yang rentan terhadap SQL Injection atau menggunakan Query Builder yang lebih aman. Dari hasil pengujian, sistem menggunakan method `where()` bawaan CodeIgniter 4 untuk mengambil data pengguna dari database.

---

## Bukti Teknis dan Mitigasi

Berikut adalah implementasi kode pada file `app/Controllers/User.php`:

# Berikut bukti
<img width="1076" height="798" alt="Screenshot 2026-04-28 135210" src="https://github.com/user-attachments/assets/1f208e03-a579-4d38-9bfe-fe42dfa3ce9d" />

```php
$user = $model->where('useremail', $email)->first();
```

Kode tersebut menunjukkan bahwa sistem menggunakan Query Builder, bukan raw query SQL seperti:

```sql
SELECT * FROM users WHERE useremail='$email'
```

Dengan Query Builder, input pengguna diproses lebih aman karena framework membantu melakukan perlindungan terhadap karakter berbahaya yang dapat menyebabkan SQL Injection.

---

## Analisis Hasil

Penggunaan method `->where()` memastikan bahwa input email dari pengguna hanya diproses sebagai data pencarian biasa, bukan sebagai perintah SQL tambahan.

Meskipun pengguna memasukkan karakter khusus atau payload berbahaya seperti SQL Injection, framework tidak akan langsung mengeksekusinya sebagai query mentah. Hal ini membuat sistem login menjadi lebih aman dan mengurangi risiko akses ilegal ke akun admin.

---

## Kesimpulan

Melalui eksperimen ini, saya memahami bahwa SQL Injection merupakan ancaman serius dalam keamanan web, terutama pada fitur login. Namun, penggunaan framework seperti CodeIgniter 4 dapat membantu mencegah serangan tersebut melalui fitur Query Builder.

Sebagai developer, kita harus memastikan setiap input pengguna diproses dengan aman dan tidak menggunakan query manual yang rentan. Dengan demikian, keamanan sistem dapat terjaga dan data penting tetap terlindungi.

---

## Referensi

* CodeIgniter 4 User Guide: Database Query Builder
* OWASP Foundation: SQL Injection Prevention
* Dokumentasi PHP dan MySQL
* Tugas UTS Pemrograman Web
# UTS-PEMROGRAMAN-WEB
# Bukti Plagiarism
<img width="1900" height="1010" alt="Screenshot 2026-04-28 140319" src="https://github.com/user-attachments/assets/7bf06590-2e2c-4107-bee9-f9ca5f117cd8" />
