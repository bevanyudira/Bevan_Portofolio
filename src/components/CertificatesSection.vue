<template>
  <section id="certificates" class="certificates">
    <div class="container">
      <h2 class="section-title">Certificates & Achievements</h2>
      <p class="section-subtitle">Professional certifications and accomplishments</p>

      <div class="certificates-grid">
        <div
          class="certificate-card"
          v-for="cert in certificates"
          :key="cert.id"
          @click="openCertificate(cert)"
        >
          <div
            class="certificate-image"
            :class="{ 'pdf-placeholder': cert.type === 'pdf' && !cert.thumbnail }"
          >
            <!-- Jika ada thumbnail (untuk gambar atau PDF dengan screenshot) -->
            <img v-if="cert.thumbnail" :src="cert.thumbnail" :alt="cert.title" />

            <!-- Jika PDF tanpa thumbnail, tampilkan iframe preview (bisa lambat) -->
            <iframe
              v-else-if="cert.type === 'pdf'"
              :src="cert.file + '#toolbar=0&navpanes=0&scrollbar=0'"
              class="pdf-preview"
              scrolling="no"
            ></iframe>

            <div class="certificate-overlay">
              <span class="zoom-icon">🔍</span>
            </div>
          </div>
          <div class="certificate-info">
            <h4>{{ cert.title }}</h4>
            <p>{{ cert.issuer }}</p>
            <span class="year">{{ cert.year }}</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal for Certificate Preview -->
    <Teleport to="body">
      <Transition name="modal">
        <div v-if="selectedCertificate" class="cert-modal-overlay" @click="closeCertificate">
          <div class="cert-modal-container" @click.stop>
            <button class="cert-modal-close" @click="closeCertificate">✕</button>

            <div class="cert-modal-content">
              <h3>{{ selectedCertificate.title }}</h3>
              <p class="cert-issuer">
                {{ selectedCertificate.issuer }} • {{ selectedCertificate.year }}
              </p>

              <div class="cert-viewer">
                <!-- PDF Viewer -->
                <iframe
                  v-if="selectedCertificate.type === 'pdf'"
                  :src="selectedCertificate.file"
                  class="pdf-viewer"
                  frameborder="0"
                ></iframe>

                <!-- Image Viewer -->
                <img
                  v-else
                  :src="selectedCertificate.file"
                  :alt="selectedCertificate.title"
                  class="image-viewer"
                />
              </div>

              <div class="cert-actions">
                <a :href="selectedCertificate.file" target="_blank" class="btn-download">
                  📥 Download / Open in New Tab
                </a>
              </div>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const selectedCertificate = ref(null)
const certificates = ref([])

// Fungsi untuk parse filename dan extract metadata
const parseFileName = (filename) => {
  // Remove extension
  const nameWithoutExt = filename.replace(/\.(pdf|jpg|jpeg|png|gif|webp)$/i, '')

  // Split by dash or underscore
  const parts = nameWithoutExt.split(/[-_]/)

  // Extract year (4 digit number)
  const yearMatch = parts.find((part) => /^\d{4}$/.test(part))
  const year = yearMatch || new Date().getFullYear().toString()

  // Remove year from parts
  const partsWithoutYear = parts.filter((part) => part !== yearMatch)

  // Last part (or last 2 parts joined) adalah issuer
  // First parts adalah title
  let title = ''
  let issuer = ''

  if (partsWithoutYear.length >= 2) {
    // Ambil 2 bagian terakhir sebagai issuer (atau 1 jika hanya ada 2 parts)
    const issuerParts = partsWithoutYear.length > 3 ? 2 : 1
    issuer = partsWithoutYear.slice(-issuerParts).join(' ')
    title = partsWithoutYear.slice(0, -issuerParts).join(' ')
  } else {
    title = partsWithoutYear.join(' ')
    issuer = 'Certificate'
  }

  return {
    title: title || 'Certificate',
    issuer: issuer || 'Unknown',
    year,
  }
}

// Fungsi untuk load certificates dari folder
const loadCertificates = () => {
  // Data sertifikat dengan metadata manual untuk akurasi
  // Untuk PDF: tambahkan thumbnailUrl dengan path ke screenshot/thumbnail image
  const certificateData = [
    {
      filename: 'Certificate Detail - CODEPOLITAN.pdf',
      title: 'Belajar Dasar HTML',
      issuer: 'Codepolitan',
      year: '2025',
      thumbnailUrl: null, // Tambahkan path ke thumbnail jika ada, contoh: '/sertif/thumbnails/cert1.jpg'
    },
    {
      filename: 'img_d63fed3f4400d34e75b5539f7a842a90.png',
      title: 'Certified Developer',
      issuer: 'Alibaba Cloud',
      year: '2024',
    },
    {
      filename: 'sertifikat_course_251_3786683_080525220554.pdf',
      title: 'Belajar Dasar Cloud dan Gen AI di AWS',
      issuer: 'Dicoding',
      year: '2025',
      thumbnailUrl: null,
    },
    {
      filename: 'sertifikat_course_600_3786683_041024123545.pdf',
      title: 'Belajar Dasar Structured Query Language (SQL)',
      issuer: 'Dicoding',
      year: '2024',
      thumbnailUrl: null,
    },
    {
      filename: 'sertifikat_course_615_3786683_190924192348.pdf',
      title: 'Belajar Dasar Data Science',
      issuer: 'Dicoding',
      year: '2024',
      thumbnailUrl: null,
    },
    {
      filename: 'sertifikat_course_653_3786683_050924223047.pdf',
      title: 'Belajar Dasar AI',
      issuer: 'Dicoding',
      year: '2024',
      thumbnailUrl: null,
    },
    {
      filename: 'sertifikat_course_697_3786683_051024002340.pdf',
      title: 'Belajar Strategi Pengembangan Diri',
      issuer: 'Dicoding',
      year: '2024',
      thumbnailUrl: null,
    },
    {
      filename: 'sertifikat_course_862_3786683_030825213538.pdf',
      title: 'AI Praktis untuk Produktivitas',
      issuer: 'Dicoding',
      year: '2025',
      thumbnailUrl: null,
    },
    {
      filename: 'sertifikat_course_867_3786683_050825124403.pdf',
      title: 'Belajar Penggunaan Generative AI',
      issuer: 'Dicoding',
      year: '2025',
      thumbnailUrl: null,
    },
    {
      filename: 'sertifikat_course_570_3786683_200824213738.pdf',
      title: 'Belajar Dasar Manajemen Proyek',
      issuer: 'Dicoding',
      year: '2024',
      thumbnailUrl: null,
    },
  ]

  certificates.value = certificateData.map((cert, index) => {
    const extension = cert.filename.split('.').pop().toLowerCase()
    const type = extension === 'pdf' ? 'pdf' : 'image'
    // Use import.meta.env.BASE_URL to get the correct base path for GitHub Pages
    const basePath = import.meta.env.BASE_URL || '/'
    const filePath = `${basePath}sertif/${cert.filename}`

    return {
      id: index + 1,
      title: cert.title,
      issuer: cert.issuer,
      year: cert.year,
      type,
      file: filePath,
      thumbnail: type === 'image' ? filePath : cert.thumbnailUrl || null,
    }
  })
}

const openCertificate = (cert) => {
  selectedCertificate.value = cert
  document.body.style.overflow = 'hidden'
}

const closeCertificate = () => {
  selectedCertificate.value = null
  document.body.style.overflow = 'auto'
}

// Load certificates saat component mounted
onMounted(() => {
  loadCertificates()
})
</script>

<style scoped>
.certificates {
  padding: 6rem 2rem;
  background: rgba(10, 10, 15, 0.8);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-title {
  font-size: 3rem;
  font-weight: 800;
  text-align: center;
  margin-bottom: 1rem;
  background: linear-gradient(135deg, #fff, #00ff88);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  position: relative;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -15px;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 4px;
  background: linear-gradient(135deg, #00ffff, #00ff88);
  border-radius: 2px;
}

.section-subtitle {
  text-align: center;
  color: rgba(255, 255, 255, 0.6);
  font-size: 1.1rem;
  margin-bottom: 4rem;
}

.certificates-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2.5rem;
  margin-top: 3rem;
}

.certificate-card {
  background: rgba(20, 20, 30, 0.6);
  border-radius: 15px;
  overflow: hidden;
  border: 1px solid rgba(0, 255, 136, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
}

.certificate-card:hover {
  transform: translateY(-10px) scale(1.02);
  border-color: rgba(0, 255, 136, 0.5);
  box-shadow: 0 20px 50px rgba(0, 255, 136, 0.2);
}

.certificate-image {
  position: relative;
  width: 100%;
  height: 220px;
  overflow: hidden;
  background: rgba(30, 30, 40, 0.8);
}

.certificate-image.pdf-placeholder {
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(30, 30, 40, 0.9);
}

.pdf-preview {
  width: 100%;
  height: 100%;
  border: none;
  pointer-events: none;
  transform: scale(1.2);
  transform-origin: top center;
}

.certificate-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
  opacity: 0.9;
}

.certificate-card:hover .certificate-image img {
  transform: scale(1.1);
  opacity: 1;
}

.certificate-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 255, 136, 0.85);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.certificate-card:hover .certificate-overlay {
  opacity: 1;
}

.zoom-icon {
  font-size: 3rem;
  animation: zoom-pulse 1s infinite;
}

@keyframes zoom-pulse {
  0%,
  100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.2);
  }
}

.certificate-info {
  padding: 1.5rem;
  text-align: center;
}

.certificate-info h4 {
  color: #fff;
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
  font-weight: 700;
}

.certificate-info p {
  color: #00ff88;
  font-size: 0.95rem;
  margin-bottom: 0.5rem;
  font-weight: 500;
}

.certificate-info .year {
  display: inline-block;
  background: rgba(0, 255, 136, 0.2);
  color: #00ff88;
  padding: 0.3rem 1rem;
  border-radius: 15px;
  font-size: 0.85rem;
  font-weight: 600;
  border: 1px solid rgba(0, 255, 136, 0.3);
}

@media (max-width: 768px) {
  .certificates-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .certificates {
    padding: 4rem 1.5rem;
  }

  .section-title {
    font-size: 2.5rem;
  }

  .certificate-image {
    height: 180px;
  }

  .certificate-info {
    padding: 1.2rem;
  }

  .certificate-info h4 {
    font-size: 1.1rem;
  }
}

/* Modal Styles */
.cert-modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.95);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10000;
  padding: 2rem;
  overflow-y: auto;
}

.cert-modal-container {
  background: rgba(20, 20, 30, 0.95);
  border-radius: 20px;
  width: 90%;
  max-width: 1000px;
  max-height: 90vh;
  position: relative;
  border: 1px solid rgba(0, 255, 136, 0.3);
  box-shadow: 0 30px 80px rgba(0, 255, 136, 0.2);
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.cert-modal-close {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  width: 45px;
  height: 45px;
  border-radius: 50%;
  background: rgba(255, 0, 0, 0.2);
  border: 2px solid rgba(255, 0, 0, 0.5);
  color: #fff;
  font-size: 1.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.cert-modal-close:hover {
  background: rgba(255, 0, 0, 0.4);
  transform: rotate(90deg);
}

.cert-modal-content {
  padding: 2rem;
  overflow-y: auto;
  flex: 1;
}

.cert-modal-content h3 {
  color: #fff;
  font-size: 1.8rem;
  margin-bottom: 0.5rem;
  font-weight: 700;
}

.cert-issuer {
  color: #00ff88;
  font-size: 1.1rem;
  margin-bottom: 2rem;
  font-weight: 500;
}

.cert-viewer {
  background: rgba(30, 30, 40, 0.5);
  border-radius: 10px;
  overflow: hidden;
  margin-bottom: 2rem;
  border: 1px solid rgba(0, 255, 136, 0.2);
}

.pdf-viewer {
  width: 100%;
  height: 600px;
  border: none;
}

.image-viewer {
  width: 100%;
  height: auto;
  display: block;
  max-height: 600px;
  object-fit: contain;
}

.cert-actions {
  display: flex;
  gap: 1rem;
  justify-content: center;
}

.btn-download {
  display: inline-block;
  padding: 0.8rem 2rem;
  background: linear-gradient(135deg, #00ffff, #00ff88);
  color: #0a0a0f;
  text-decoration: none;
  border-radius: 10px;
  font-weight: 700;
  transition: all 0.3s ease;
  border: none;
  cursor: pointer;
}

.btn-download:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 30px rgba(0, 255, 136, 0.4);
}

/* Modal Transitions */
.modal-enter-active,
.modal-leave-active {
  transition: all 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .cert-modal-container,
.modal-leave-to .cert-modal-container {
  transform: scale(0.9);
  opacity: 0;
}

@media (max-width: 768px) {
  .cert-modal-container {
    width: 95%;
    max-height: 95vh;
  }

  .cert-modal-content {
    padding: 1.5rem;
  }

  .cert-modal-content h3 {
    font-size: 1.4rem;
  }

  .pdf-viewer,
  .image-viewer {
    height: 400px;
  }

  .cert-modal-close {
    top: 1rem;
    right: 1rem;
    width: 40px;
    height: 40px;
  }
}
</style>
