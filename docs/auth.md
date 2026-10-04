# Autentikasi Lingkungan Pasaree

- Semua backend memvalidasi JWT dengan `aud` tepat `pasaree`.
- Compose menyetel `JWT_AUD=pasaree` untuk backend.
- Token antar layanan untuk proksi Lumbung disimpan sebagai rahasia CI, bukan di berkas.
