# Runbook Infra Pasaree

1. `docker compose up --build` untuk jalan lokal penuh.
2. Cadangan volume `pasaree-db` tiap hari.
3. Bila backend 401 massal, periksa `JWT_AUD` harus `pasaree`.
4. Bila web tidak dapat backend, periksa `PASAREE_API_BASE_URL`.
5. Rilis: tandai versi, pastikan CI hijau, lalu umumkan di TownHall.
