# TIKpedia Backend

Backend ini disiapkan agar Flutter dapat memakai PostgreSQL melalui REST API.

## 1. Jalankan PostgreSQL

Pastikan Docker Desktop terpasang, lalu dari folder `backend`:

```bash
docker compose up -d
```

## 2. Buat tabel dan data awal

Jika `psql` tersedia:

```bash
psql postgresql://tikpedia:tikpedia@localhost:5432/tikpedia -f schema.sql
```

Atau buka PostgreSQL client/pgAdmin dan jalankan isi `schema.sql`.

## 3. Jalankan API

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

pip install -r requirements.txt
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

API tersedia di `http://127.0.0.1:8000` dan dokumentasi otomatis di `/docs`.

## 4. Catatan Android

Jika Flutter dijalankan di Android Emulator, alamat backend dari emulator adalah:

`http://10.0.2.2:8000`

Untuk HP fisik, gunakan alamat IP komputer pada jaringan Wi-Fi yang sama, misalnya `http://192.168.1.10:8000`.

Flutter saat ini masih memakai `AppState` demo agar UI bisa dijalankan tanpa backend. Setelah backend hidup, layer API dapat menggantikan sumber data demo tanpa mengubah halaman UI.
