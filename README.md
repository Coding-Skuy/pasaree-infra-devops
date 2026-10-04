# pasaree-infra-devops

Infrastruktur Marketplace Pasaree. Divisi Pasaree (Marketplace), org Coding-Skuy. Template Opsi A.

Rujukan utama: [Pasaree-TownHall](https://github.com/Coding-Skuy/Pasaree-TownHall).

## Cakupan

- Compose lokal: backend Rust, Postgres `pasaree`, web lapak.
- Alur CI: periksa mobile, web, backend, model, pipa, token desain.
- Basis data `pasaree` terpisah. Tidak berbagi dengan divisi lain.

## Mulai Cepat

1. Salin `.env.example` menjadi `.env`.
2. Jalankan `docker compose up --build`.
3. Backend di `http://localhost:8101/kesehatan`. Web di `http://localhost:8102`.

Lihat `docs/runbook.md` untuk operasional dan `docs/auth.md` untuk aturan JWT.
