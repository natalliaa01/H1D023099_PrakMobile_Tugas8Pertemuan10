# TokoKita (Tugas 8 Pertemuan 10)

Aplikasi Flutter untuk latihan CRUD UI pada produk, sesuai tugas Pertemuan 10.  
UI telah diselesaikan hingga tuntas dan setiap halaman sudah ditambahkan nama panggilan Natalia pada AppBar seperti instruksi.

---

## Data Diri
-   **Nama:** `Natalia Nidya Fidelia`
-   **NIM:** `H1D023099`
-   **Shift Baru:** `E`
-   **Shift Asal:** `B`

## Screenshot Aplikasi

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

## Alur Navigasi Aplikasi

```
Login Page
   ↓
Registrasi Page (opsional)
   ↓
List Produk Natalia
   ↓
Tambah Produk Natalia / Detail Produk Natalia
   ↓
Edit / Delete
   ↓
Logout → kembali ke Login Page
```

---

## Struktur Project

```
lib/
 ├─ main.dart
 ├─ model/
 │   └─ produk.dart
 ├─ ui/
 │   ├─ login_page.dart
 │   ├─ registrasi_page.dart
 │   ├─ produk_page.dart
 │   ├─ produk_form.dart
 │   └─ produk_detail.dart
 └─ bloc/
     └─ produk_bloc.dart
```

---

## Penjelasan Kode Per Halaman

### `main.dart`
- Entry point aplikasi
- Menjalankan `MaterialApp`
- Home diarahkan ke `ProdukPage()`

```dart
return const MaterialApp(
  title: 'Toko Kita Natalia',
  debugShowCheckedModeBanner: false,
  home: ProdukPage(),
);
```

---

### `login_page.dart`

**Fungsi utama:**
- Form login (email & password)
- Validasi input wajib
- Tombol login menuju List Produk

```dart
Navigator.pushReplacement(
  context,
  MaterialPageRoute(builder: (context) => const ProdukPage()),
);
```

---

### `registrasi_page.dart`

**Fitur & validasi:**
- Nama minimal 3 karakter
- Email format valid
- Password min 6 karakter
- Konfirmasi password wajib sama

AppBar:
```dart
title: const Text("Registrasi Natalia"),
```

---

### `produk_page.dart` (List Produk Natalia)

**Isi halaman:**
- Menampilkan list produk statis (dummy)
- Tombol + membuka form tambah produk
- Drawer berisi Logout

AppBar:
```dart
title: const Text('List Produk Natalia'),
```

Logout:
```dart
Navigator.pushAndRemoveUntil(
  context,
  MaterialPageRoute(builder: (context) => const LoginPage()),
  (route) => false,
);
```

---

### `produk_form.dart` (Tambah / Edit)

**Fungsi:**
- Form input kode, nama, harga
- Bisa Tambah atau Edit tergantung `widget.produk`

Logika judul:
```dart
if (widget.produk != null) {
  judul = "UBAH PRODUK Natalia";
} else {
  judul = "TAMBAH PRODUK Natalia";
}
```

---

### `produk_detail.dart`

**Menampilkan:**
- kode produk
- nama produk
- harga

Tombol tindakan:
- EDIT → buka ProdukForm dengan data lama
- DELETE → dialog konfirmasi

```dart
OutlinedButton(
  child: const Text("DELETE"),
  onPressed: () => confirmHapus(),
)
```

---

## Cara Menjalankan Aplikasi

```bash
flutter pub get
flutter run
```
---
