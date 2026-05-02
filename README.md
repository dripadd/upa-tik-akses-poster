# Poster QR — Log Akses Ruang Server UPA TIK

Static page untuk generate & print poster QR Code akses ruang server UPA TIK (internal use).

**Live URL:** https://dripadd.github.io/upa-tik-akses-poster/

## Fitur

- 🎨 Poster A5 portrait, branded UPA TIK (biru langit `#0290d9` + merah `#c1272d`)
- 📱 QR Code auto-generated via [api.qrserver.com](https://api.qrserver.com)
- 🖨️ Print-ready (`@page A5 portrait`, margin 8mm)
- ⬇️ Download QR PNG (untuk pakai di tempat lain)
- ⚙️ Editor inline: ganti URL Web App tanpa edit code
- 💡 Instruksi pemakaian + tips first-time scan

## Cara Pakai

1. Buka https://dripadd.github.io/upa-tik-akses-poster/
2. (Opsional) Edit URL Web App di field konfigurasi → klik "Update QR" — kalau URL Web App berubah
3. Klik **Print A5** untuk print langsung, atau **Download QR PNG** untuk simpan QR doang
4. Print warna A5 → laminating → tempel di pintu ruang server

## Backend

Web App + Sheets backend ada di Apps Script project terpisah. Defense in depth: Google OAuth + admin whitelist email + warning untuk domain di luar organisasi. URL Web App di-default di code untuk convenience admin.

## Stack

- HTML / CSS inline (no framework, no build)
- QR generator: api.qrserver.com (free, no auth)
- Hosting: GitHub Pages

## License

Internal use UPA TIK.
