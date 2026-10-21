# Evaluasi Pembelajaran MILEA – Report Generator

Web app untuk membuat lembar **Evaluasi Pelatihan** (PDF 1 halaman) dari ekspor survei MILEA (format memanjang: satu baris per pertanyaan; kolom `question`, `answer`, `point`).

## Struktur

```
index.html          ← seluruh aplikasi
api/summarize.js    ← Vercel Function: meringkas masukan peserta lewat GitHub Models
package.json
```

## Aturan perhitungan

- Nilai memakai kolom `point` (label jawaban diabaikan; ketidaksesuaian label–point ditampilkan sebagai peringatan).
- Rata-rata item dibulatkan 2 desimal; rata-rata kelompok = rata-rata dari nilai item yang sudah dibulatkan.
- Semua baris di file dihitung (seluruh materi/survey_title).

## Environment Variables (Vercel)

| Nama | Wajib | Keterangan |
|---|---|---|
| `GITHUB_MODELS_TOKEN` | Ya, untuk fitur AI | Fine-grained PAT GitHub dengan izin **Models: Read-only** (boleh sama dengan app LEAP) |
| `GITHUB_MODELS_MODEL` | Tidak | Default `openai/gpt-4.1-mini` |

Tanpa token, tombol AI disembunyikan dan tombol **Rapikan** (tanpa AI) tetap tersedia.
