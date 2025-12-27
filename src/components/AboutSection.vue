<template>
  <section id="about" class="about">
    <div class="container">
      <h2 class="section-title">About Me</h2>
      <div class="about-content">
        <div class="about-text">
          <p class="description">
            Saya adalah seorang Backend Developer yang berfokus pada pengembangan aplikasi
            menggunakan Laravel. Saya berpengalaman dalam membangun sistem backend yang stabil,
            aman, dan scalable, mulai dari perancangan arsitektur, pengolahan data, hingga integrasi
            API. Dalam pengembangan aplikasi, saya biasa menggunakan MySQL sebagai database utama,
            mengelola relasi data dengan efektif, dan memastikan performa query tetap optimal.
            Selain itu, saya juga terbiasa mengimplementasikan autentikasi, middleware, REST API,
            serta pengelolaan deployment dengan baik.
          </p>

          <div class="info-grid">
            <div class="info-card">
              <div class="icon">📧</div>
              <h3>Contact</h3>
              <p>aureliusbevanyudirapalevi@mail.ugm.ac.id</p>
              <p>+62 896-4918-5614</p>
            </div>

            <div class="info-card">
              <div class="icon">📍</div>
              <h3>Location</h3>
              <p>Jawa Tengah, Indonesia</p>
              <p>Undergraduate Student</p>
            </div>
          </div>
        </div>

        <div class="education">
          <h3 class="subsection-title">
            <span class="icon">🎓</span>
            Education History
          </h3>
          <div class="timeline">
            <div class="timeline-item">
              <div class="timeline-dot"></div>
              <div class="timeline-content">
                <h4>Software Engineering Technology</h4>
                <p class="institution">Universitas Gadjah Mada</p>
                <p class="year">2023 - Present</p>
                <p class="description-edu">Focus on Software Engineering and Database Systems.</p>
              </div>
            </div>

            <div class="timeline-item">
              <div class="timeline-dot"></div>
              <div class="timeline-content">
                <h4>Senior High School</h4>
                <p class="institution">SMA Negeri 1 Karanganyar</p>
                <p class="year">2020 - 2023</p>
                <p class="description-edu">Science Major with focus on Mathematics and Physics</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup></script>

<style scoped>
.about {
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
  margin-bottom: 3rem;
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

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  margin-top: 4rem;
}

.about-text .description {
  font-size: 1.1rem;
  line-height: 1.8;
  color: rgba(255, 255, 255, 0.8);
  margin-bottom: 2.5rem;
  text-align: justify;
}

.info-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
}

.info-card {
  background: rgba(20, 20, 30, 0.6);
  padding: 2rem;
  border-radius: 15px;
  border: 1px solid rgba(0, 255, 255, 0.2);
  transition: all 0.3s ease;
}

.info-card:hover {
  transform: translateY(-5px);
  border-color: rgba(0, 255, 255, 0.5);
  box-shadow: 0 10px 30px rgba(0, 255, 255, 0.2);
}

.info-card .icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.info-card h3 {
  color: #00ffff;
  margin-bottom: 1rem;
  font-size: 1.2rem;
}

.info-card p {
  color: rgba(255, 255, 255, 0.7);
  margin: 0.3rem 0;
  font-size: 0.95rem;
}

.subsection-title {
  font-size: 1.8rem;
  color: #fff;
  margin-bottom: 2rem;
  display: flex;
  align-items: center;
  gap: 0.8rem;
}

.subsection-title .icon {
  font-size: 2rem;
}

.timeline {
  position: relative;
  padding-left: 2rem;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(180deg, #00ffff, #00ff88);
}

.timeline-item {
  position: relative;
  margin-bottom: 2.5rem;
  padding-left: 2rem;
}

.timeline-item:last-child {
  margin-bottom: 0;
}

.timeline-dot {
  position: absolute;
  left: -2.6rem;
  top: 0;
  width: 12px;
  height: 12px;
  background: #00ffff;
  border-radius: 50%;
  box-shadow: 0 0 0 4px rgba(0, 255, 255, 0.2);
  animation: pulse-dot 2s infinite;
}

@keyframes pulse-dot {
  0%,
  100% {
    box-shadow: 0 0 0 4px rgba(0, 255, 255, 0.2);
  }
  50% {
    box-shadow: 0 0 0 8px rgba(0, 255, 255, 0.1);
  }
}

.timeline-content {
  background: rgba(20, 20, 30, 0.6);
  padding: 1.5rem;
  border-radius: 10px;
  border-left: 3px solid #00ffff;
  transition: all 0.3s ease;
}

.timeline-content:hover {
  background: rgba(20, 20, 30, 0.8);
  transform: translateX(5px);
}

.timeline-content h4 {
  color: #00ff88;
  font-size: 1.3rem;
  margin-bottom: 0.5rem;
}

.timeline-content .institution {
  color: #fff;
  font-weight: 600;
  margin-bottom: 0.3rem;
}

.timeline-content .year {
  color: #00ffff;
  font-size: 0.9rem;
  margin-bottom: 0.8rem;
}

.timeline-content .description-edu {
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.6;
  font-size: 0.95rem;
}

@media (max-width: 968px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .info-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .about {
    padding: 4rem 1.5rem;
  }

  .section-title {
    font-size: 2.5rem;
  }

  .subsection-title {
    font-size: 1.5rem;
  }

  .timeline {
    padding-left: 1.5rem;
  }

  .timeline-item {
    padding-left: 1.5rem;
  }

  .timeline-dot {
    left: -2.35rem;
  }
}
</style>
