# 📱 SantriKoding - Fullstack Express.js & React Native CRUD

Aplikasi CRUD (Create, Read, Update, Delete) lengkap berbasis **Express.js REST API** dan **React Native**, dilengkapi fitur upload gambar via *multipart/form-data* dan validasi request.

---

## 🛠️ Tech Stack

### Backend (`backend-express`)
- **Runtime & Framework**: [Node.js](https://nodejs.org/), [Express.js](https://expressjs.com/)
- **ORM & Database**: [Prisma ORM](https://www.prisma.io/), [MySQL](https://www.mysql.com/)
- **File Upload**: [Multer](https://github.com/expressjs/multer)
- **Validation**: [express-validator](https://express-validator.github.io/)
- **CORS & Middleware**: [cors](https://www.npmjs.com/package/cors), [body-parser](https://www.npmjs.com/package/body-parser)

### Frontend (`ReactNative/LearnReactNative`)
- **Framework**: [React Native](https://reactnative.dev/) (CLI)
- **Navigation**: [@react-navigation/native-stack](https://reactnavigation.org/)
- **HTTP Client**: [Axios](https://axios-http.com/)
- **Media Picker**: [react-native-image-picker](https://github.com/react-native-image-picker/react-native-image-picker)
- **Environment Management**: [react-native-dotenv](https://www.npmjs.com/package/react-native-dotenv)

---

## ✨ Fitur Utama

- **Read Posts**: Menampilkan daftar seluruh postingan dengan thumbnail foto, judul, serta tombol aksi.
- **Create Post**: Menambahkan postingan baru dengan upload foto dari galeri perangkat.
- **Edit & Update Post**: Memuat detail postingan ke dalam form dan memperbarui data beserta opsi penggantian foto.
- **Delete Post**: Menghapus postingan dari database sekaligus menghapus file foto terkait di server.
- **Validation Handling**: Penanganan validasi input baik dari sisi backend maupun pesan error pada UI mobile.

---

## 📂 Struktur Direktori

```text
santrikoding/
├── backend-express/             # REST API Backend
│   ├── controllers/             # PostController (CRUD Logic)
│   ├── middlewares/             # Upload middleware (Multer)
│   ├── prisma/                  # Schema Prisma & Migrations
│   ├── routes/                  # Express API Routes
│   ├── uploads/                 # Direktori penyimpanan file gambar
│   ├── utils/                   # Validasi request (express-validator)
│   └── index.js                 # Entry point server Express
│
└── ReactNative/
    └── LearnReactNative/       # Mobile Frontend App
        ├── android/             # Android native code & config
        ├── src/
        │   ├── navigations/     # React Navigation Stack
        │   ├── screens/posts/   # Screen Index, Create, Edit
        │   ├── services/        # Axios instance & API config
        │   ├── styles/          # Reusable Stylesheet
        │   └── utils/           # Helper format error validation
        └── App.tsx              # Root component
```

---

## 🚀 Panduan Menjalankan Proyek

### 1. Menjalankan Backend Express

1. Masuk ke direktori `backend-express`:
   ```bash
   cd backend-express
   ```
2. Install dependensi:
   ```bash
   npm install
   ```
3. Konfigurasi file `.env`:
   ```env
   DATABASE_URL="mysql://root:@localhost:3306/db_express"
   ```
4. Jalankan migrasi Prisma (pastikan database MySQL sudah berjalan, misal via XAMPP):
   ```bash
   npx prisma migrate dev
   ```
5. Jalankan server:
   ```bash
   node index.js
   ```
   *Server akan berjalan di `http://localhost:3000`.*

---

### 2. Menjalankan Frontend React Native

1. Masuk ke direktori aplikasi mobile:
   ```bash
   cd ReactNative/LearnReactNative
   ```
2. Install dependensi:
   ```bash
   npm install
   ```
3. Konfigurasi file `.env`:
   - Untuk **Android Emulator**:
     ```env
     BACKEND_API_URL=http://10.0.2.2:3000
     ```
   - Untuk **Device Fisik (HP)** via Wi-Fi/IP LAN:
     ```env
     BACKEND_API_URL=http://<IP_KOMPUTER_ANDA>:3000
     ```
4. Hubungkan port forwarding adb (opsional jika menggunakan emulator):
   ```bash
   adb reverse tcp:3000 tcp:3000
   adb reverse tcp:8081 tcp:8081
   ```
5. Jalankan aplikasi di Android:
   ```bash
   npm run android
   ```

---

## 📡 Daftar Endpoint REST API

| Method | Endpoint | Deskripsi |
|---|---|---|
| `GET` | `/api/posts` | Mengambil seluruh daftar postingan |
| `POST` | `/api/posts` | Menambahkan postingan baru (multipart) |
| `GET` | `/api/posts/:id` | Mengambil detail postingan berdasarkan ID |
| `PUT` | `/api/posts/:id` | Memperbarui postingan berdasarkan ID |
| `DELETE` | `/api/posts/:id` | Menghapus postingan berdasarkan ID |

---

## 📄 Lisensi
Tutorial dan referensi materi oleh [SantriKoding.com](https://santrikoding.com).
Dikembangkan untuk keperluan pembelajaran.
