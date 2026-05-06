# Poster QR — Log Akses Ruang Server UPA TIK UNRI

Static page untuk generate & print poster QR Code akses ruang server UPA TIK UNRI (internal use).

**Live URL:** https://dripadd.github.io/upa-tik-akses-poster/

**QR target:** https://cekipsaya.com/akses-server/

## Fitur (v2.0)

- 🎨 Poster A5 portrait, branded UPA TIK UNRI (biru langit `#0290d9` + merah `#c1272d`)
- 📱 QR Code auto-generated via [api.qrserver.com](https://api.qrserver.com) — Level H error correction (30%)
- 🇮🇩 **Logo UNRI embed di tengah QR** — branded look, scannable di Level H ECC
- 🌈 **5 pilihan warna QR**: Hitam (default, B&W print), Biru UPA TIK, Hijau UNRI, Merah UNRI, Abu Gelap
- 🖨️ Print-ready (`@page A5 portrait`, margin 8mm)
- ⬇️ Download QR PNG (canvas-based, logo built-in)
- ⚙️ Editor inline: ganti URL, warna, resolusi tanpa edit code
- 💡 Instruksi pemakaian + tips multi-browser/multi-device

## Cara Pakai

1. Buka https://dripadd.github.io/upa-tik-akses-poster/
2. (Opsional) Customize:
   - **URL**: default `https://cekipsaya.com/akses-server/`
   - **Resolusi QR**: 400/600/800 px
   - **Warna QR**: 5 pilihan
   - **Logo Tengah**: UNRI / tanpa logo
3. Klik **🖨 Print A5** untuk print langsung, atau **⬇ Download QR PNG** untuk simpan
4. Print A5 → laminating → tempel di pintu ruang server

## Architecture (v2.0 — Tier 2)

QR target URL `cekipsaya.com/akses-server/` adalah static HTML form yang POST ke Apps Script via PHP proxy. Bypass Chrome multi-account redirect issue + works di all browsers/devices/accounts.

```
User scan QR → cekipsaya.com/akses-server/ (static HTML)
                     ↓ JS fetch POST (same-origin, no CORS)
            cekipsaya.com/akses-server/submit.php (PHP proxy)
                     ↓ curl POST (server-to-server)
            script.google.com/macros/s/.../exec (Apps Script doPost)
                     ↓ processForm() → write
            Sheet (PRIVATE, owner-only access)
```

**Defense in depth**: Sheet restricted access (admin only) + Execute as owner + email format validation + tipe user (INTERNAL/EKSTERNAL) auto-classify + dual-mode (Google session OR manual input).

## Backend

Web App + Sheets backend ada di Apps Script project (kuswara@staff.unri.ac.id). Form di-host di cekipsaya.com untuk solve cross-browser issue (Chrome multi-account auto-redirect, iOS Safari ITP, Apps Script CORS).

Cross-browser confirmed: Chrome (UNRI/Gmail) + Safari iOS + Firefox + Edge — all work.

## Stack

- HTML / CSS / Canvas inline (no framework, no build)
- QR generator: api.qrserver.com (Level H error correction untuk safe logo embed)
- Logo overlay: HTML5 Canvas (client-side composition)
- Hosting: GitHub Pages (poster generator) + cekipsaya.com (form proxy) + Apps Script (backend)

## License

Internal use UPA TIK UNRI.
