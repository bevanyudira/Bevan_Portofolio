# Portfolio Website - Bevan

Portfolio website profesional dengan tema dark yang modern dan responsif untuk Backend Developer.

## 🎨 Fitur

- ✨ **Desain Modern Dark Theme** - Tema gelap dengan gradient cyan-green yang eye-catching
- 📱 **Fully Responsive** - Tampilan optimal di semua ukuran layar
- 🎯 **Single Page Application** - Semua konten dalam satu halaman dengan smooth scrolling
- 🧭 **Smooth Navigation** - Navbar dengan animasi smooth scroll ke setiap section
- 💫 **Animasi Interaktif** - Hover effects, transitions, dan animasi yang engaging
- ⚡ **Performance Optimized** - Build dengan Vite untuk kecepatan maksimal

## 📋 Sections

### 1. **Home / Hero Section**

- Tampilan nama dan role (Backend Developer)
- Code snippet interaktif
- CTA buttons untuk navigasi cepat
- Scroll indicator animasi

### 2. **About Me**

- Deskripsi personal
- Informasi kontak (Email, Phone)
- Lokasi dan availability
- Timeline riwayat pendidikan

### 3. **Skills**

- Grid display framework & teknologi
- Icon/emoji untuk setiap skill
- Hover effects yang menarik
- Kategori untuk setiap teknologi

### 4. **Projects**

- Gallery project dengan gambar
- Deskripsi setiap project
- Tags teknologi yang digunakan
- Hover overlay untuk detail

### 5. **Certificates**

- Showcase sertifikasi profesional
- Gambar sertifikat dengan zoom effect
- Detail issuer dan tahun

### 6. **Footer**

- Quick links
- Social media links
- Copyright info

## 🎨 Color Scheme

- **Primary Background**: `#0a0a0f` (Hitam gelap)
- **Secondary Background**: `#14141e` (Dark slate)
- **Accent Cyan**: `#00ffff`
- **Accent Green**: `#00ff88`
- **Gradient**: Linear gradient dari cyan ke green

## 🛠️ Teknologi

- **Vue 3** - Framework JavaScript modern
- **Vite** - Build tool yang super cepat
- **CSS3** - Untuk styling dan animasi
- **Responsive Design** - Mobile-first approach

## 📦 Instalasi

1. Clone repository atau pastikan Anda berada di folder project

2. Install dependencies:

```bash
npm install
```

3. **PENTING**: Pastikan Node.js version Anda >= 20.19.0 atau >= 22.12.0

   Cek versi Node.js:

   ```bash
   node --version
   ```

   Jika versi Anda di bawah requirement, upgrade Node.js dari: https://nodejs.org/

4. Jalankan development server:

```bash
npm run dev
```

5. Build untuk production:

```bash
npm run build
```

## 📝 Kustomisasi

### Mengubah Data Personal

#### 1. **Hero Section** ([src/components/HeroSection.vue](src/components/HeroSection.vue))

- Ubah nama di bagian `<h1 class="name">`
- Ubah role di `<h2 class="role">`
- Ubah tagline sesuai keinginan

#### 2. **About Section** ([src/components/AboutSection.vue](src/components/AboutSection.vue))

- Edit deskripsi personal
- Ubah email, phone, dan lokasi
- Update riwayat pendidikan

#### 3. **Skills Section** ([src/components/SkillsSection.vue](src/components/SkillsSection.vue))

- Modifikasi array `skills` di `<script setup>`
- Tambah/hapus teknologi sesuai keahlian Anda

#### 4. **Projects Section** ([src/components/ProjectsSection.vue](src/components/ProjectsSection.vue))

- Update array `projects` dengan project Anda
- Ganti URL gambar dengan screenshot project asli
- Edit judul, deskripsi, dan tags

#### 5. **Certificates Section** ([src/components/CertificatesSection.vue](src/components/CertificatesSection.vue))

- Update array `certificates`
- Ganti gambar dengan foto sertifikat asli

### Mengubah Warna

Edit file [src/assets/base.css](src/assets/base.css) di bagian `:root`:

```css
:root {
  --bg-primary: #0a0a0f; /* Background utama */
  --accent-cyan: #00ffff; /* Warna accent cyan */
  --accent-green: #00ff88; /* Warna accent green */
}
```

## 📱 Responsive Breakpoints

- **Desktop**: > 968px
- **Tablet**: 768px - 968px
- **Mobile**: < 768px

## 🚀 Deploy

Setelah build, folder `dist` berisi static files yang siap di-deploy ke:

- Vercel
- Netlify
- GitHub Pages
- Atau hosting lainnya

## 💡 Tips

1. **Gambar Project**: Gunakan gambar dengan resolusi minimal 800x600px untuk hasil terbaik
2. **Sertifikat**: Scan sertifikat dengan kualitas tinggi
3. **SEO**: Update meta tags di [index.html](index.html)
4. **Social Media**: Tambahkan link social media asli di Footer component

## 📄 Struktur File

```
src/
├── components/
│   ├── Navbar.vue              # Navigation bar
│   ├── HeroSection.vue         # Home section
│   ├── AboutSection.vue        # About section
│   ├── SkillsSection.vue       # Skills section
│   ├── ProjectsSection.vue     # Projects section
│   ├── CertificatesSection.vue # Certificates section
│   └── Footer.vue              # Footer
├── assets/
│   ├── base.css               # Base styles & theme
│   └── main.css               # Main styles
├── App.vue                    # Root component
└── main.js                    # Entry point
```

## 🎯 Fitur Tambahan yang Bisa Ditambahkan

- [ ] Dark/Light theme toggle
- [ ] Form kontak dengan EmailJS
- [ ] Blog section
- [ ] Testimonials
- [ ] Download CV button
- [ ] Loading animation
- [ ] Particle.js background effect
- [ ] Internationalization (i18n) untuk multi-bahasa

## 📞 Support

Jika ada pertanyaan atau butuh bantuan, silakan hubungi atau buat issue di repository.

---

**Made with ❤️ using Vue 3 + Vite**
