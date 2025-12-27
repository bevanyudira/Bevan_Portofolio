<template>
  <section id="projects" class="projects">
    <div class="container">
      <h2 class="section-title">My Projects</h2>
      <p class="section-subtitle">Some of my recent work</p>

      <div class="projects-grid">
        <div
          class="project-card"
          v-for="project in projects"
          :key="project.id"
          @click="openModal(project)"
        >
          <div class="project-image">
            <img :src="project.image" :alt="project.title" />
            <div class="project-overlay">
              <span class="view-details">View Details</span>
            </div>
          </div>
          <div class="project-content">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <div class="project-tags">
              <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal Detail -->
    <Teleport to="body">
      <Transition name="modal">
        <div v-if="selectedProject" class="modal-overlay" @click="closeModal">
          <div class="modal-container" @click.stop>
            <button class="modal-close" @click="closeModal">✕</button>

            <div class="modal-content">
              <div class="modal-image">
                <img :src="selectedProject.image" :alt="selectedProject.title" />
              </div>

              <div class="modal-info">
                <h2>{{ selectedProject.title }}</h2>

                <div class="modal-tags">
                  <span v-for="tag in selectedProject.tags" :key="tag" class="tag">{{ tag }}</span>
                </div>

                <div class="modal-description">
                  <h3>📋 Description</h3>
                  <p>{{ selectedProject.description }}</p>
                </div>

                <div class="modal-details">
                  <h3>🔧 Technical Details</h3>
                  <ul>
                    <li v-for="detail in selectedProject.details" :key="detail">{{ detail }}</li>
                  </ul>
                </div>

                <div class="modal-features">
                  <h3>✨ Key Features</h3>
                  <ul>
                    <li v-for="feature in selectedProject.features" :key="feature">
                      {{ feature }}
                    </li>
                  </ul>
                </div>

                <div class="modal-links" v-if="selectedProject.github || selectedProject.demo">
                  <a
                    v-if="selectedProject.github"
                    :href="selectedProject.github"
                    target="_blank"
                    class="btn-link"
                  >
                    💻 View Code
                  </a>
                  <a
                    v-if="selectedProject.demo"
                    :href="selectedProject.demo"
                    target="_blank"
                    class="btn-link"
                  >
                    🚀 Live Demo
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const selectedProject = ref(null)

const projects = ref([
  {
    id: 1,
    title: 'Sistem Informasi Masyarakat',
    description:
      'Sistem Informasi Masyarakat (SIMAS) adalah platform manajemen digital untuk administrasi RT/RW yang mengelola data warga, iuran, keuangan, dan program kerja. Sistem ini melayani berbagai role pengguna mulai dari Super Admin, Admin RW, Admin RT, hingga warga dengan fitur pembayaran digital terintegrasi.',
    image: 'https://res.cloudinary.com/dbhluqpi3/image/upload/v1766824775/sirtrw_iioqnu.png',
    tags: ['Laravel', 'MySQL', 'Bootstrap', 'Axios'],
    details: [
      'Backend API menggunakan Laravel 10 dengan arsitektur RESTful',
      'Database MySQL dengan relasi kompleks untuk multi-level organisasi (RW/RT)',
      'Autentikasi dan otorisasi menggunakan Laravel Sanctum dengan JWT token',
      'Payment gateway terintegrasi dengan Midtrans untuk pembayaran digital',
      'Frontend menggunakan Blade template engine dengan Bootstrap 5',
      'Visualisasi data menggunakan Chart.js untuk dashboard analytics',
      'API documentation dengan Swagger/L5-Swagger',
      'Real-time data fetching menggunakan Axios HTTP client',
      'DataTables untuk manajemen tabel data yang kompleks',
      'Factory dan Seeder untuk development environment',
    ],
    features: [
      'Sistem autentikasi multi-role (Super Admin, Admin RW, Admin RT, Ketua RW, Ketua RT, Warga)',
      'Manajemen data warga lengkap dengan aktivasi akun',
      'Sistem iuran digital dengan tracking pembayaran real-time',
      'Manajemen program kerja RT/RW dengan upload gambar',
      'Laporan keuangan komprehensif (pemasukan dan pengeluaran)',
      'Dashboard analytics dengan visualisasi grafik pie, bar, dan line chart',
      'Dompet digital untuk transaksi internal warga',
      'Sistem kritik dan saran dengan tracking status',
      'Checkout dan pembayaran terintegrasi Midtrans',
      'Riwayat pembayaran dan mutasi keuangan',
      'Export laporan untuk dokumentasi',
      'Responsive design untuk akses mobile dan desktop',
    ],
    github: '#',
    demo: '#',
  },
  {
    id: 2,
    title: 'Sistem Informasi Pajak Bumi dan Bangunan',
    description:
      'Platform web full-stack yang mentransformasi pengelolaan PBB secara digital, menggantikan proses manual pemerintah daerah dengan sistem terpusat yang efisien. Sistem ini melayani petugas pajak untuk mengelola data properti dan menerbitkan SPPT, serta memungkinkan wajib pajak mengecek tagihan secara online.',
    image: 'https://res.cloudinary.com/dbhluqpi3/image/upload/v1766818997/ipbb_dp1wmm.png',
    tags: ['FastAPI', 'MySQL', 'SQLAlchemy', 'GeoPandas'],
    details: [
      'Arsitektur full-stack dengan backend FastAPI (Python 3.12) dan frontend Next.js 19',
      'Database MySQL 8.0 dengan migrasi Alembic untuk version control',
      'Integrasi GIS untuk visualisasi peta properti menggunakan Shapefile',
      'Google OAuth 2.0 untuk autentikasi dan otorisasi yang aman',
      'Containerisasi dengan Docker dan Docker Compose untuk deployment',
      'Reverse proxy Traefik v3.0 untuk routing dan load balancing',
      'TypeScript untuk type safety di frontend dengan React 19',
      'RESTful API design dengan validasi Pydantic',
    ],
    features: [
      'Dashboard analitik dengan KPI real-time (target pajak, pembayaran, tren)',
      'Manajemen objek pajak digital (SPOP) dengan Nomor Objek Pajak (NOP) unik',
      'Kalkulasi otomatis Nilai Jual Objek Pajak (NJOP) dan PBB terutang',
      'Penerbitan dan pencetakan SPPT massal atau individual',
      'Portal publik untuk wajib pajak mengecek tagihan dengan NOP',
      'Visualisasi peta properti terintegrasi dengan data GIS',
      'Manajemen pengguna dengan role-based access control (Admin/User)',
      'Import data shapefile untuk integrasi data geografis',
    ],
    github: '#',
    demo: '#',
  },
  {
    id: 3,
    title: 'Notes App',
    description:
      'Aplikasi REST API manajemen catatan berbasis Laravel dengan sistem autentikasi, kategori, tags, dan attachments. Dilengkapi dengan dokumentasi Swagger interaktif, frontend Vue.js, containerization Docker, serta monitoring stack (Prometheus & Grafana) untuk production-ready deployment.',
    image: 'https://res.cloudinary.com/dbhluqpi3/image/upload/v1766818997/notes_app_e1xcrn.png',
    tags: ['Laravel', 'Vue.js', 'MySQL', 'Docker'],
    details: [
      'Dibangun menggunakan Laravel 11 (PHP 8.2) dengan arsitektur RESTful API',
      'MySQL 8.0 untuk database relational dengan optimasi foreign key constraints',
      'Redis untuk caching dan session management',
      'Laravel Sanctum untuk autentikasi berbasis token JWT',
      'Swagger/OpenAPI (L5-Swagger) untuk dokumentasi API interaktif',
      'Vue.js 3 dengan Pinia state management dan Vue Router untuk frontend',
      'TailwindCSS dan Flowbite untuk UI components modern',
      'Docker & Docker Compose untuk containerization multi-service',
      'Monitoring stack: Prometheus untuk metrics collection, Grafana untuk visualisasi, cAdvisor untuk container monitoring',
      'Nginx sebagai web server dalam Docker environment',
      'GitLab CI/CD untuk automated testing dan deployment pipeline',
      'PHPUnit untuk unit testing dengan coverage reports',
    ],
    features: [
      'Sistem autentikasi lengkap (register, login, logout) dengan token-based authentication',
      'CRUD manajemen catatan dengan support multiple attachments per note',
      'Sistem kategorisasi dan tagging untuk organisasi catatan yang fleksibel',
      'Advanced search dan filtering berdasarkan kategori, tags, dan warna',
      'Pagination dengan parameter kustom untuk performa optimal',
      'Upload dan manajemen file attachment dengan validasi tipe dan ukuran',
      'Auto-generate slug untuk tags dan categories',
      'User isolation - setiap user hanya dapat mengakses data miliknya sendiri',
      'Dokumentasi API interaktif menggunakan Swagger UI',
      'Frontend SPA dengan Vue.js 3 untuk interface yang responsif',
      'Real-time monitoring dashboard dengan Grafana untuk CPU, memory, dan network metrics',
      'Docker deployment dengan 7 layanan terorkestra (app, database, redis, monitoring stack)',
      'Database management interface via PHPMyAdmin',
      'Automated database migrations dan seeders untuk setup cepat',
    ],
    github: '#',
    demo: '#',
  },
  {
    id: 4,
    title: 'Stunting Detection',
    description:
      'Aplikasi web untuk deteksi dan monitoring stunting pada anak menggunakan standar WHO. Sistem ini membantu tenaga kesehatan dalam melakukan screening cepat status gizi anak berdasarkan tinggi badan terhadap umur dengan perhitungan Z-score otomatis.',
    image: 'https://res.cloudinary.com/dbhluqpi3/image/upload/v1766818997/stunting_hsom28.png',
    tags: ['Laravel', 'MySQL', 'Bootstrap', 'Axios'],
    details: [
      'Dibangun dengan Laravel 11 sebagai backend framework',
      'Database SQLite untuk penyimpanan data yang ringan dan portabel',
      'Frontend menggunakan Bootstrap 5 dengan tampilan modern dan responsive',
      'RESTful API dengan JSON response untuk integrasi yang mudah',
      'Eloquent ORM untuk manajemen database yang efisien',
      'Implementasi standar antropometri WHO (World Health Organization)',
      'Axios untuk komunikating asynchronous dengan API',
      'Form validation untuk memastikan data yang akurat',
      'Real-time calculation dengan Z-score algorithm',
    ],
    features: [
      'Input data anak (nama, jenis kelamin, umur, tinggi badan)',
      'Perhitungan otomatis Z-score berdasarkan standar WHO',
      'Deteksi status gizi: Normal, Stunting, Stunting Berat, atau Tinggi',
      'Riwayat pengukuran dengan tabel interaktif',
      'Interface yang user-friendly dengan gradient modern',
      'Toast notification untuk feedback user',
      'Responsive design untuk berbagai ukuran layar',
      'Data seeder standar WHO untuk berbagai umur dan jenis kelamin',
      'Filter data berdasarkan gender dan umur',
      'Dokumentasi API lengkap',
    ],
    github: '#',
    demo: '#',
  },
  {
    id: 5,
    title: 'Katalog Buku Digital',
    description:
      'REST API dan Web Application untuk sistem manajemen katalog buku digital dengan fitur autentikasi dan otorisasi menggunakan Laravel Sanctum. Setiap pengguna dapat mengelola koleksi buku pribadi mereka dengan sistem CRUD yang lengkap dan aman.',
    image: 'https://res.cloudinary.com/dbhluqpi3/image/upload/v1766818997/buku_hffwhd.png',
    tags: ['Laravel', 'MySQL', 'Tailwind'],
    details: [
      'Framework Laravel 11.x dengan PHP 8.2+',
      'Authentication menggunakan Laravel Sanctum untuk token-based API',
      'Database MySQL dengan migration dan seeder',
      'Dual interface: RESTful API dan Web Application',
      'Blade templating engine dengan Tailwind CSS untuk UI',
      'Docker containerization untuk development environment',
      'Postman collection siap pakai untuk API testing',
      'Middleware authorization untuk resource protection',
    ],
    features: [
      'Sistem autentikasi lengkap (Register, Login, Logout)',
      'CRUD operations untuk manajemen buku (Create, Read, Update, Delete)',
      'Authorization berbasis kepemilikan (user hanya dapat mengelola buku miliknya)',
      'RESTful API dengan JSON response terstandarisasi',
      'Web interface responsive dengan Tailwind CSS',
      'Validasi input untuk semua form',
      'Database seeder dengan data sample Indonesia',
      'Docker support untuk kemudahan deployment',
      'Session management dan CSRF protection',
      'API documentation dengan Postman collection',
    ],
    github: '#',
    demo: '#',
  },
  {
    id: 6,
    title: 'Movie App',
    description:
      'Aplikasi web katalog film interaktif yang memungkinkan pengelolaan data film lengkap dengan fitur CRUD (Create, Read, Update, Delete), dilengkapi dengan sistem autentikasi dan middleware untuk keamanan akses.',
    image: 'https://res.cloudinary.com/dbhluqpi3/image/upload/v1766825909/movie_edv3qg.png',
    tags: ['Laravel', 'Blade'],
    details: [
      'Dibangun menggunakan Laravel 11 dengan arsitektur MVC (Model-View-Controller)',
      'PHP 8.2 sebagai bahasa pemrograman backend',
      'Blade Template Engine untuk rendering view yang dinamis',
      'Vite sebagai build tool untuk asset bundling dan development server',
      'RESTful routing dengan implementasi resource controller',
      'Middleware custom untuk autentikasi dan autorisasi pengguna',
      'Composer untuk dependency management',
    ],
    features: [
      'Katalog film dengan informasi lengkap (judul, deskripsi, tanggal rilis, cast, genre, poster)',
      'Sistem CRUD untuk manajemen data film (tambah, lihat, edit, hapus)',
      'Halaman detail film dengan informasi cast dan genre yang terstruktur',
      'Proteksi route menggunakan middleware autentikasi',
      'Interface yang user-friendly dengan Blade components',
      'Form validation untuk input data film',
      'Tampilan grid responsif untuk katalog film',
      'Integrasi dengan TMDB image API untuk poster film',
    ],
    github: '#',
    demo: '#',
  },
  {
    id: 7,
    title: 'ToDo List App',
    description:
      'Aplikasi ToDo List modern yang dibangun dengan Vue.js 3 menggunakan Composition API, dilengkapi dengan pipeline CI/CD untuk deployment otomatis. Aplikasi ini memungkinkan pengguna untuk mengelola daftar tugas harian dengan antarmuka yang responsif dan interaktif.',
    image: 'https://res.cloudinary.com/dbhluqpi3/image/upload/v1766825908/TODOlist_hld1ey.png',
    tags: ['Vue.js', 'CI/CD'],
    details: [
      'Dibangun menggunakan Vue.js 3 dengan Composition API dan script setup',
      'Vite sebagai build tool untuk development yang cepat dan optimized production build',
      'ESLint dan Prettier untuk code quality dan konsistensi formatting',
      'Reactive data management menggunakan Vue Composition API (ref)',
      'Modern CSS dengan responsive design dan smooth transitions',
      'CI/CD pipeline untuk automated deployment',
      'Hot Module Replacement (HMR) untuk development experience yang optimal',
    ],
    features: [
      'Tambah tugas baru dengan input form yang user-friendly',
      'Tandai tugas sebagai selesai dengan checkbox interaktif',
      'Hapus tugas yang tidak diperlukan dengan tombol remove',
      'Visual feedback untuk tugas yang sudah diselesaikan (strikethrough effect)',
      'UI/UX yang clean dan modern dengan hover effects',
      'Responsive design yang dapat diakses dari berbagai perangkat',
      'Real-time update tanpa reload halaman',
      'Local state management untuk performa optimal',
    ],
    github: '#',
    demo: '#',
  },
  {
    id: 8,
    title: 'Obesity Prediction System',
    description:
      'Sistem prediksi level obesitas berbasis machine learning dengan 5 algoritma berbeda, mencapai akurasi hingga 95%. Aplikasi full-stack yang mengintegrasikan Laravel sebagai backend dan Flask sebagai microservice ML, dilengkapi dengan riwayat prediksi pasien dan perbandingan performa model secara real-time.',
    image: 'https://res.cloudinary.com/dbhluqpi3/image/upload/v1766828902/obesity_aianm0.png',
    tags: [
      'Laravel',
      'Flask',
      'scikit-learn',
      'MySQL',
      'Tailwind CSS',
      'Machine Learning',
      'Alpine.js',
    ],
    details: [
      'Dibangun dengan arsitektur microservices memisahkan web service (Laravel) dan ML service (Flask)',
      'Backend menggunakan Laravel 11 dengan PHP 8.3+ dan routing RESTful API',
      'Machine Learning service menggunakan Flask dan scikit-learn dengan 5 model terlatih',
      'Database MySQL untuk menyimpan riwayat prediksi dengan audit trail lengkap',
      'Frontend responsive menggunakan Tailwind CSS 3.x dan Alpine.js untuk interaktivitas',
      'Vite sebagai build tool untuk optimisasi asset compilation',
      'Model ML dilatih dengan preprocessing menggunakan StandardScaler dan LabelEncoder',
      'Implementasi CORS untuk komunikasi cross-origin antara Laravel dan Flask',
    ],
    features: [
      'Prediksi level obesitas menggunakan 5 algoritma ML (Logistic Regression, KNN, Decision Tree, Random Forest, AdaBoost)',
      'Random Forest mencapai akurasi tertinggi 95.22% dengan precision 95.27%',
      'Klasifikasi ke dalam 7 kategori obesitas dari Insufficient Weight hingga Obesity Type III',
      'Riwayat prediksi pasien dengan timestamp dan detail input lengkap',
      'Dashboard perbandingan performa semua model secara visual',
      'Form input interaktif dengan validasi real-time',
      'Health check endpoint untuk monitoring status ML service',
      'Responsive design yang optimal untuk desktop dan mobile',
      'RESTful API untuk integrasi dengan sistem eksternal',
    ],
    github: '#',
    demo: '#',
  },
])

const openModal = (project) => {
  selectedProject.value = project
  document.body.style.overflow = 'hidden'
}

const closeModal = () => {
  selectedProject.value = null
  document.body.style.overflow = 'auto'
}
</script>

<style scoped>
.projects {
  padding: 6rem 2rem;
  background: rgba(15, 15, 20, 0.5);
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
  background: linear-gradient(135deg, #fff, #00ffff);
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

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2.5rem;
  margin-top: 3rem;
}

.project-card {
  background: rgba(20, 20, 30, 0.6);
  border-radius: 15px;
  overflow: hidden;
  border: 1px solid rgba(0, 255, 255, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
}

.project-card:hover {
  transform: translateY(-10px);
  border-color: rgba(0, 255, 255, 0.4);
  box-shadow: 0 20px 50px rgba(0, 255, 255, 0.2);
}

.project-image {
  position: relative;
  width: 100%;
  height: 250px;
  overflow: hidden;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.project-card:hover .project-image img {
  transform: scale(1.1);
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 255, 255, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.view-details {
  color: #0a0a0f;
  font-weight: 700;
  font-size: 1.1rem;
  padding: 1rem 2rem;
  background: #fff;
  border-radius: 50px;
}

.project-content {
  padding: 2rem;
}

.project-content h3 {
  color: #fff;
  font-size: 1.5rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.project-content p {
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.6;
  margin-bottom: 1.5rem;
  font-size: 0.95rem;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  background: rgba(0, 255, 255, 0.1);
  color: #00ffff;
  padding: 0.4rem 1rem;
  border-radius: 20px;
  font-size: 0.85rem;
  border: 1px solid rgba(0, 255, 255, 0.3);
  font-weight: 500;
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .projects {
    padding: 4rem 1.5rem;
  }

  .section-title {
    font-size: 2.5rem;
  }

  .project-image {
    height: 200px;
  }

  .project-content {
    padding: 1.5rem;
  }

  .project-content h3 {
    font-size: 1.3rem;
  }
}

/* Modal Styles */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.85);
  backdrop-filter: blur(10px);
  z-index: 9999;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  overflow-y: auto;
}

.modal-container {
  background: rgba(20, 20, 30, 0.95);
  border-radius: 20px;
  max-width: 900px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
  border: 1px solid rgba(0, 255, 255, 0.3);
  box-shadow: 0 20px 60px rgba(0, 255, 255, 0.3);
}

.modal-close {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  background: rgba(255, 255, 255, 0.1);
  border: none;
  color: #fff;
  font-size: 1.5rem;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  z-index: 10;
}

.modal-close:hover {
  background: rgba(0, 255, 255, 0.2);
  transform: rotate(90deg);
}

.modal-content {
  display: flex;
  flex-direction: column;
}

.modal-image {
  width: 100%;
  height: 400px;
  overflow: hidden;
  border-radius: 20px 20px 0 0;
}

.modal-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.modal-info {
  padding: 3rem;
}

.modal-info h2 {
  font-size: 2.5rem;
  background: linear-gradient(135deg, #fff, #00ffff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 1.5rem;
}

.modal-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
  margin-bottom: 2rem;
}

.modal-tags .tag {
  background: rgba(0, 255, 255, 0.15);
  color: #00ffff;
  padding: 0.6rem 1.2rem;
  border-radius: 25px;
  font-size: 0.9rem;
  border: 1px solid rgba(0, 255, 255, 0.4);
  font-weight: 600;
}

.modal-description,
.modal-details,
.modal-features {
  margin-bottom: 2rem;
}

.modal-info h3 {
  color: #00ff88;
  font-size: 1.3rem;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.modal-description p {
  color: rgba(255, 255, 255, 0.8);
  line-height: 1.8;
  font-size: 1.05rem;
}

.modal-details ul,
.modal-features ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.modal-details li,
.modal-features li {
  color: rgba(255, 255, 255, 0.8);
  padding: 0.8rem 0;
  padding-left: 2rem;
  position: relative;
  line-height: 1.6;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.modal-details li:last-child,
.modal-features li:last-child {
  border-bottom: none;
}

.modal-details li::before,
.modal-features li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: #00ffff;
  font-size: 1.2rem;
}

.modal-links {
  display: flex;
  gap: 1rem;
  margin-top: 2rem;
  padding-top: 2rem;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.btn-link {
  flex: 1;
  padding: 1rem 2rem;
  background: linear-gradient(135deg, #00ffff, #00ff88);
  color: #0a0a0f;
  text-decoration: none;
  border-radius: 50px;
  font-weight: 700;
  text-align: center;
  transition: all 0.3s ease;
  box-shadow: 0 5px 20px rgba(0, 255, 255, 0.3);
}

.btn-link:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 30px rgba(0, 255, 255, 0.5);
}

/* Modal Transitions */
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

.modal-enter-active .modal-container,
.modal-leave-active .modal-container {
  transition: transform 0.3s ease;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  transform: scale(0.9);
}

/* Responsive Modal */
@media (max-width: 768px) {
  .modal-overlay {
    padding: 1rem;
  }

  .modal-image {
    height: 250px;
  }

  .modal-info {
    padding: 2rem 1.5rem;
  }

  .modal-info h2 {
    font-size: 2rem;
  }

  .modal-info h3 {
    font-size: 1.1rem;
  }

  .modal-links {
    flex-direction: column;
  }
}
</style>
