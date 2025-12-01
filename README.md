# **📄 README.md — TokoKita (Flutter + CodeIgniter 4)**
Tugas Praktikum Pengenalan Framework — Pertemuan 10 & 11  
Aplikasi Flutter dengan fitur **Login, Registrasi, dan CRUD Produk** terintegrasi dengan API **CodeIgniter 4**.

---

## 👤 **Data Diri**
| Keterangan | Isi |
|----------|-----|
| **Nama** | Natalia Nidya Fidelia |
| **NIM** | H1D023099 |
| **Shift Baru** | E |
| **Shift Asal** | B |

---


### Login Page
<img width="162" height="360" alt="Image" src="https://github.com/user-attachments/assets/ead1095e-5993-404f-a362-0352cf802561" />

### Registrasi Page
<img width="162" height="360" alt="Image" src="https://github.com/user-attachments/assets/ab9bade1-bd5a-418f-be2e-8b2c81ecc45f" />

### List Produk Natalia
<img width="162" height="360" alt="Image" src="https://github.com/user-attachments/assets/98ece797-b2e6-46ed-8d47-5c2e94effdfb" />

### Tambah Produk Natalia
<img width="162" height="360" alt="Image" src="https://github.com/user-attachments/assets/c63264e9-b9e6-422c-aa9b-623d082d4fe8" />

### Detail Produk Natalia
<img width="162" height="360" alt="Image" src="https://github.com/user-attachments/assets/7eed0bc7-6776-4293-93bc-c7702d07590a" />

### Edit Produk Natalia
<img width="162" height="360" alt="Image" src="https://github.com/user-attachments/assets/11325a0f-b53f-493d-9b85-7cb339744281" />

### Logout Page
<img width="162" height="360" alt="Image" src="https://github.com/user-attachments/assets/6dd3d22b-ce2b-4165-b485-a54dcb5a0844" />
---

# 🔀 **Alur Navigasi Aplikasi**

```
Login Page
   ↓
Registrasi Page (opsional)
   ↓
List Produk Natalia
   ↓
Tambah Produk Natalia / Detail Produk Natalia
   ↓
Edit / Delete Produk
   ↓
Logout → Kembali ke Login Page
```

---

# 📁 **Struktur Project Flutter**

```
lib/
 ├─ main.dart
 ├─ model/
 │   ├─ login.dart
 │   ├─ registrasi.dart
 │   └─ produk.dart
 ├─ bloc/
 │   ├─ login_bloc.dart
 │   ├─ registrasi_bloc.dart
 │   └─ produk_bloc.dart
 ├─ helpers/
 │   ├─ api.dart
 │   ├─ api_url.dart
 │   └─ user_info.dart
 └─ ui/
     ├─ login_page.dart
     ├─ registrasi_page.dart
     ├─ produk_page.dart
     ├─ produk_form.dart
     └─ produk_detail.dart
```

---

# 🔑 **LOGIN — Proses & Penjelasan**

1. User memasukkan email & password  
2. Flutter mengirim request:
   ```
   POST /login
   Content-Type: application/x-www-form-urlencoded
   ```
3. Jika sukses → menerima token  
4. Token disimpan di `SharedPreferences`

---

# 📝 **REGISTRASI — Proses & Penjelasan**

Flow:
- Input **nama, email, password**
- Flutter → API via:
  ```
  POST /registrasi
  ```
- Password di-hash  
- Simpan DB  
- Response:
  ```json
  {"code":200,"status":true,"data":"Registrasi Berhasil"}
  ```

---

# 📦 **CRUD PRODUK — Penjelasan Lengkap**

### ➕ Tambah Produk
```
POST /produk
Authorization: Bearer <token>
```

### 📄 List Produk
```
GET /produk
```

### ✏️ Update Produk
```
PUT /produk/{id}
```

### 🗑️ Delete Produk
```
DELETE /produk/{id}
```

---

# 🛠️ **ROUTES Backend CI4**
```php
$routes->post('registrasi', 'RegistrasiController::registrasi');
$routes->post('login', 'LoginController::login');

$routes->group('produk', function ($routes) {
    $routes->get('/', 'ProdukController::list');
    $routes->post('/', 'ProdukController::create');
    $routes->get('(:segment)', 'ProdukController::detail/$1');
    $routes->put('(:segment)', 'ProdukController::ubah/$1');
    $routes->delete('(:segment)', 'ProdukController::hapus/$1');
});
```

---

# **Cara Menjalankan**

## Backend (CI4)
```bash
php spark serve --host 0.0.0.0 --port 8080
```

## Flutter
```bash
flutter pub get
flutter run
```

---

# 🎯 **Pertemuan 11 — Integrasi API**

### Screenshot:
![img1](https://github.com/user-attachments/assets/7edeb5e2-bf79-4c7d-9d16-1a5fa9f94b4c)
![img2](https://github.com/user-attachments/assets/2aea6498-7b79-4365-9d68-3f09fe99e5f0)
![img3](https://github.com/user-attachments/assets/b203945f-49cf-4c71-9ba3-be1672f38118)
