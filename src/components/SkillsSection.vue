<template>
  <section id="skills" class="skills">
    <div class="container">
      <h2 class="section-title">Skills & Technologies</h2>
      <p class="section-subtitle">Tools and frameworks I work with</p>

      <div class="skills-grid">
        <div class="skill-card" v-for="skill in skills" :key="skill.name">
          <div class="skill-icon">
            <img :src="skill.logo" :alt="skill.name" />
          </div>
          <h3>{{ skill.name }}</h3>
          <p>{{ skill.category }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const skills = ref([
  {
    name: 'HTML5',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg',
    category: 'Markup',
  },
  {
    name: 'CSS3',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg',
    category: 'Styling',
  },
  {
    name: 'JavaScript',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg',
    category: 'Language',
  },
  {
    name: 'PHP',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg',
    category: 'Language',
  },
  {
    name: 'Python',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg',
    category: 'Language',
  },
  {
    name: 'Vue.js',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg',
    category: 'Framework',
  },
  {
    name: 'Tailwind CSS',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/tailwindcss/tailwindcss-original.svg',
    category: 'CSS Framework',
  },
  {
    name: 'Laravel',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/laravel/laravel-original.svg',
    category: 'Framework',
  },
  {
    name: 'FastAPI',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/fastapi/fastapi-original.svg',
    category: 'Framework',
  },
  {
    name: 'MySQL',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg',
    category: 'Database',
  },
  {
    name: 'PostgreSQL',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg',
    category: 'Database',
  },
  {
    name: 'MongoDB',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original.svg',
    category: 'Database',
  },
  {
    name: 'Docker',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg',
    category: 'DevOps',
  },
  {
    name: 'Git',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg',
    category: 'Version Control',
  },
  {
    name: 'REST API',
    logo: 'https://cdn-icons-png.flaticon.com/512/2164/2164832.png',
    category: 'Architecture',
  },
])
</script>

<style scoped>
.skills {
  padding: 6rem 2rem;
  background: rgba(10, 10, 15, 0.8);
  position: relative;
  overflow: hidden;
}

.skills::before {
  content: '';
  position: absolute;
  top: 0;
  left: -50%;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, rgba(0, 255, 136, 0.05) 0%, transparent 70%);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
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

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
  margin-top: 3rem;
}

.skill-card {
  background: rgba(20, 20, 30, 0.6);
  padding: 2rem;
  border-radius: 15px;
  text-align: center;
  border: 1px solid rgba(0, 255, 255, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.skill-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(0, 255, 255, 0.1), transparent);
  transition: left 0.5s ease;
}

.skill-card:hover::before {
  left: 100%;
}

.skill-card:hover {
  transform: translateY(-10px);
  border-color: rgba(0, 255, 255, 0.5);
  box-shadow: 0 15px 40px rgba(0, 255, 255, 0.2);
  background: rgba(20, 20, 30, 0.8);
}

.skill-icon {
  width: 80px;
  height: 80px;
  margin: 0 auto 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: float 3s ease-in-out infinite;
}

.skill-icon img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  filter: drop-shadow(0 0 10px rgba(0, 255, 255, 0.3));
  transition: all 0.3s ease;
}

.skill-card:hover .skill-icon img {
  filter: drop-shadow(0 0 20px rgba(0, 255, 255, 0.6));
  transform: scale(1.1);
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.skill-card:nth-child(even) .skill-icon {
  animation-delay: 1s;
}

.skill-card h3 {
  color: #fff;
  font-size: 1.3rem;
  margin-bottom: 0.5rem;
  font-weight: 600;
}

.skill-card p {
  color: #00ffff;
  font-size: 0.9rem;
  font-weight: 500;
}

@media (max-width: 640px) {
  .skills {
    padding: 4rem 1.5rem;
  }

  .section-title {
    font-size: 2.5rem;
  }

  .skills-grid {
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 1.5rem;
  }

  .skill-card {
    padding: 1.5rem;
  }

  .skill-icon {
    width: 60px;
    height: 60px;
  }

  .skill-card h3 {
    font-size: 1.1rem;
  }
}
</style>
