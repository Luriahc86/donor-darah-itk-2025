# 🚀 Deployment Guide - Vercel

Panduan untuk deploy aplikasi Donor Darah ITK ke Vercel.

## 📋 Prasyarat

1. Akun Vercel (gratis) - [Daftar di vercel.com](https://vercel.com)
2. Git repository (GitHub, GitLab, atau Bitbucket)
3. Vercel CLI (opsional) atau gunakan dashboard Vercel

## 🔧 Method 1: Deploy via Vercel Dashboard (Recommended)

### Langkah-langkah:

1. **Push kode ke Git Repository**
   ```bash
   git add .
   git commit -m "Prepare for Vercel deployment"
   git push origin main
   ```

2. **Login ke Vercel**
   - Buka [vercel.com](https://vercel.com)
   - Login dengan akun GitHub/GitLab/Bitbucket

3. **Import Project**
   - Klik "Add New..." → "Project"
   - Pilih repository `Donor-Darah-ITK`
   - Klik "Import"

4. **Configure Project**
   Vercel akan otomatis mendeteksi:
   - Framework: Vite
   - Build Command: `npm run build`
   - Output Directory: `dist`
   - Install Command: `npm install`

5. **Deploy**
   - Klik "Deploy"
   - Tunggu proses build selesai (biasanya 1-2 menit)
   - Aplikasi siap diakses!

## 🖥️ Method 2: Deploy via Vercel CLI

### Instalasi Vercel CLI

```bash
npm install -g vercel
```

### Deploy

```bash
# Login ke Vercel
vercel login

# Deploy (production)
vercel --prod

# Atau deploy preview
vercel
```

## ✅ Verifikasi

Setelah deployment berhasil, Anda akan mendapatkan:
- URL Production: `https://donor-darah-itk.vercel.app` (atau custom domain)
- URL Preview: untuk setiap push ke branch

## 🔄 Auto-Deploy

Setiap kali Anda push ke repository, Vercel akan otomatis:
- Build ulang aplikasi
- Deploy ke production (jika push ke branch main)
- Deploy preview (jika push ke branch lain)

## 🛠️ Troubleshooting

### Build Error
Jika ada error saat build:
1. Test build secara lokal terlebih dahulu:
   ```bash
   npm run build
   ```
2. Periksa error log di Vercel dashboard
3. Pastikan semua dependencies sudah ada di `package.json`

### Routing Issue (404 pada refresh)
Masalah ini sudah ditangani dengan konfigurasi `vercel.json`:
```json
{
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ]
}
```

## 📝 Environment Variables

Jika aplikasi membutuhkan environment variables:
1. Buka Project Settings di Vercel Dashboard
2. Pilih "Environment Variables"
3. Tambahkan variabel yang diperlukan

## 🎉 Selesai!

Aplikasi Donor Darah ITK siap diakses secara online!
