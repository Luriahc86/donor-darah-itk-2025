# 🔧 Build Fix Log - Vercel Deployment

## Tanggal: 2025-12-16

### ❌ Error yang Ditemukan:

```
error during build:
Could not resolve "../assets/about-author.jpg" from "src/pages/Author.vue"
```

**Status Build**: FAILED  
**Exit Code**: 1

### 🔍 Root Cause:

Vite tidak dapat me-resolve path asset relatif (`../assets/`) saat production build. Ini terjadi karena:
- Path relatif di template tidak di-track oleh bundler  
- Vite membutuhkan import eksplisit untuk asset processing

### ✅ Solusi yang Diterapkan:

Mengubah semua referensi asset image dari **inline path** menjadi **JavaScript import**:

#### 1. File: `src/pages/Author.vue`
```vue
<!-- BEFORE -->
<img src="../assets/about-author.jpg" />

<!-- AFTER -->
<script setup>
import authorImage from '../assets/about-author.jpg';
</script>
<template>
  <img :src="authorImage" />
</template>
```

#### 2. File: `src/pages/About.vue`
```vue
<script setup>
import aboutImage from '../assets/about-image.jpg';
</script>
<template>
  <img :src="aboutImage" />
</template>
```

#### 3. File: `src/pages/Campaign.vue`
```vue
<script setup>
import kampanyeImage from '../assets/kampanye.jpeg';
import kampanyeImage2 from '../assets/kampanye_2.jpeg';
</script>
<template>
  <img :src="kampanyeImage" />
  <img :src="kampanyeImage2" />
</template>
```

#### 4. File: `src/components/Navbar.vue`
```vue
<script setup>
import logoImage from '../assets/logo.png';
</script>
<template>
  <img :src="logoImage" />
</template>
```

### 📊 Assets yang Diperbaiki:

| File | Asset |
|------|-------|
| Author.vue | about-author.jpg |
| About.vue | about-image.jpg |
| Campaign.vue | kampanye.jpeg, kampanye_2.jpeg |
| Navbar.vue | logo.png |

### ✅ Verifikasi:

- [x] Semua file Vue telah diupdate
- [x] Import statements ditambahkan
- [x] Template bindings menggunakan `:src`
- [ ] Build lokal berhasil (pending)
- [ ] Deploy Vercel berhasil (pending)

### 📝 Notes:

- URL eksternal (seperti Google Maps embed) tidak perlu diubah
- Pattern ini adalah best practice untuk Vue 3 + Vite
- Memastikan asset optimization dan fingerprinting bekerja dengan baik

### 🚀 Deploy Instructions:

1. Commit semua perubahan:
   ```bash
   git add .
   git commit -m "fix: resolve Vite asset import issues for production build"
   ```

2. Push ke repository:
   ```bash
   git push origin main
   ```

3. Vercel akan otomatis rebuild dengan fix ini

### 📚 Reference:

- [Vite Static Asset Handling](https://vitejs.dev/guide/assets.html)
- [Vue 3 Asset URLs](https://vuejs.org/guide/best-practices/production-deployment.html#asset-url)
