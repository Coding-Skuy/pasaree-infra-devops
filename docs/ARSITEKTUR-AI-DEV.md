# Arsitektur AI-dev pasaree-infra-devops

Dokumen tambahan untuk `versions/v1.0.0/docs/40-TECHSTACK.md` dan `60-BLAST-RADIUS.md` (kedua file itu beku v1.0.0 dan hanya berisi ringkasan; jangan ditimpa). Rujukan versi: [Pasaree-TownHall v1.0.0](https://github.com/Coding-Skuy/Pasaree-TownHall/blob/main/platform/versions/v1.0.0/CHANGELOG.md).

## Matriks stack dan fitur

| Aspek | Terkunci | Catatan |
|---|---|---|
| CI | GitHub Actions: `cargo test`, `bun install` + `svelte-check`, Gradle build KMP, pytest | build gagal bila test merah |
| Lokal | Docker Compose: Postgres 16 `pasaree`, backend :8101, web :8102 | |
| Secret | `DATABASE_URL`, kunci JWT, `JWT_AUD=pasaree`, service key Lumbung | tidak pernah di repo |
| Rilis mobile | Play Store + APK sideload + TestFlight | |
| Rilis web | browser saja | |
| Runbook | `docs/runbook.md`, `docs/auth.md` | |

Larangan: berbagi DB `pasaree` dengan divisi lain; menyimpan secret di repo.

| Lingkungan | Komponen | Catatan |
|---|---|---|
| lokal | Compose: db, backend :8101, web :8102 | `docker compose up --build` |
| staging/prod | backend Rust, Postgres `pasaree`, web | secret per env |

## Blast radius

Batas context repo (townhall-roadmap §2: komisi 8% transparan, escrow T+1; katalog jujur; fulfillment wajib via trip Lumbung).

Boleh disentuh:

- Workflow CI, Compose, deploy per env, secret, runbook, pemantauan.

Dilarang:

- Mengubah kode aplikasi di repo lain.
- Berbagi DB atau secret dengan divisi lain.
- Secret dalam commit.

Kontrak dikonsumsi:

- Artefak build dari enam repo pasaree lain.

Kontrak diproduksi:

- Pipeline CI/CD, image, environment, runbook.

Catatan: Pasaree tidak mengonsumsi modul `:shared:pantry-resep` (milik Pawonee). Failure utama: kontrak berubah tanpa update SRS, test tidak mengikuti acceptance criteria, rollback tidak siap. Rollback: revert commit repo ini dan kembali ke kontrak Pasaree-TownHall v1.0.0.
