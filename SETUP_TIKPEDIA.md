# TIKpedia Mobile - Panduan Mulai

Project ini sudah dibangun ulang dari template Flutter kosong mengikuti mockup TIKpedia.

## Jalankan Flutter

1. Buka folder project ini di VS Code/Android Studio.
2. Jalankan:

```bash
flutter pub get
flutter run
```

Demo login sudah aktif tanpa backend: email bebas dan password minimal 4 karakter.

## Aktifkan database/API

Database PostgreSQL dan backend FastAPI sudah disiapkan di folder `backend/`.

1. Install Docker Desktop.
2. Buka terminal pada `backend`.
3. Jalankan `docker compose up -d`.
4. Buat tabel/data dengan menjalankan `schema.sql` pada database `tikpedia`.
5. Buat virtual environment Python dan install `requirements.txt`.
6. Jalankan `uvicorn main:app --reload --host 0.0.0.0 --port 8000`.
7. Buka `http://127.0.0.1:8000/docs` untuk melihat API.
8. Setelah backend siap, ubah `useApi = false` menjadi `useApi = true` di `lib/services/app_state.dart`.

Untuk Android Emulator, `ApiService.baseUrl` sudah memakai `http://10.0.2.2:8000`.

## Catatan

Versi pertama ini sengaja menggunakan `AppState` demo sebagai fallback supaya UI dan fitur dapat dicoba tanpa database. Layer `ApiService` sudah disiapkan agar sumber data bisa dipindahkan ke FastAPI/PostgreSQL secara bertahap.

Password pada backend saat ini menggunakan SHA-256 untuk prototipe tugas. Untuk deployment nyata, gunakan password hashing seperti Argon2/bcrypt dan authentication token.
