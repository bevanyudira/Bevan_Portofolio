<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-brand">
          <h3>Aurelius Bevan</h3>
          <p>Backend Developer</p>
        </div>

        <div class="footer-links">
          <h4>Quick Links</h4>
          <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#skills">Skills</a></li>
            <li><a href="#projects">Projects</a></li>
          </ul>
        </div>

        <div class="footer-social">
          <h4>Connect</h4>
          <div class="social-icons">
            <a
              href="https://www.linkedin.com/in/bevan-yudira-b79328297"
              target="_blank"
              rel="noopener noreferrer"
              class="social-icon"
            >
              <img
                src="https://cdn-icons-png.flaticon.com/512/174/174857.png"
                alt="LinkedIn"
                class="logo-linkedin"
              />
              <span>LinkedIn</span>
            </a>
            <a href="mailto:aureliusbevanyudirapalevi@mail.ugm.ac.id" class="social-icon">
              <img
                src="https://cdn-icons-png.flaticon.com/512/561/561127.png"
                alt="Email"
                class="logo-email"
              />
              <span>aureliusbevanyudirapalevi@mail.ugm.ac.id</span>
            </a>
            <a
              href="https://github.com/bevanyudira"
              target="_blank"
              rel="noopener noreferrer"
              class="social-icon"
            >
              <img
                src="https://cdn-icons-png.flaticon.com/512/733/733553.png"
                alt="GitHub"
                class="logo-github"
              />
              <span>GitHub</span>
            </a>
          </div>
        </div>
      </div>

      <div class="footer-bottom">
        <p>&copy; 2025 Bevan. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script setup></script>

<style scoped>
.footer {
  background: rgba(5, 5, 10, 0.95);
  padding: 3rem 2rem 1.5rem;
  border-top: 1px solid rgba(0, 255, 255, 0.1);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.footer-content {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: 3rem;
  margin-bottom: 2rem;
}

.footer-brand h3 {
  font-size: 2rem;
  background: linear-gradient(135deg, #00ffff, #00ff88);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 0.5rem;
}

.footer-brand p {
  color: rgba(255, 255, 255, 0.6);
  font-size: 1.1rem;
}

.footer-links h4,
.footer-social h4 {
  color: #00ffff;
  margin-bottom: 1rem;
  font-size: 1.1rem;
}

.footer-links ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-links li {
  margin-bottom: 0.5rem;
}

.footer-links a {
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-links a:hover {
  color: #00ffff;
}

.social-icons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.social-icon {
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  transition: all 0.3s ease;
  font-size: 0.95rem;
  display: flex;
  align-items: center;
  gap: 0.8rem;
}

.social-icon img {
  width: 24px;
  height: 24px;
  object-fit: contain;
  transition: all 0.3s ease;
}

.social-icon .logo-linkedin {
  filter: brightness(0) saturate(100%) invert(50%) sepia(94%) saturate(1913%) hue-rotate(182deg)
    brightness(93%) contrast(101%);
}

.social-icon .logo-email {
  filter: brightness(0) saturate(100%) invert(100%);
}

.social-icon .logo-github {
  filter: brightness(0) saturate(100%) invert(100%);
}

.social-icon:hover {
  color: #00ff88;
  transform: translateX(5px);
}

.social-icon:hover img {
  transform: scale(1.15);
}

.social-icon:hover .logo-linkedin {
  filter: brightness(0) saturate(100%) invert(50%) sepia(94%) saturate(1913%) hue-rotate(182deg)
    brightness(110%) contrast(101%);
}

.social-icon:hover .logo-email {
  filter: brightness(0) saturate(100%) invert(78%) sepia(61%) saturate(392%) hue-rotate(93deg)
    brightness(96%) contrast(96%);
}

.social-icon:hover .logo-github {
  filter: brightness(0) saturate(100%) invert(78%) sepia(61%) saturate(392%) hue-rotate(93deg)
    brightness(96%) contrast(96%);
}

.footer-bottom {
  padding-top: 2rem;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  text-align: center;
}

.footer-bottom p {
  color: rgba(255, 255, 255, 0.5);
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
}
</style>
