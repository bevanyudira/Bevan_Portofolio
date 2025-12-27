<template>
  <section id="home" class="hero">
    <div class="hero-content">
      <div class="text-content">
        <p class="greeting">Hi, I'm</p>
        <h1 class="name">Aurelius Bevan</h1>
        <h2 class="role">Backend Developer</h2>
        <p class="tagline">Building robust and scalable server-side solutions</p>
        <div class="cta-buttons">
          <a href="#projects" class="btn btn-primary">View My Work</a>
          <a href="#about" class="btn btn-secondary">About Me</a>
        </div>
      </div>
      <div class="hero-visual">
        <div class="code-block">
          <div class="code-header">
            <span class="dot red"></span>
            <span class="dot yellow"></span>
            <span class="dot green"></span>
          </div>
          <div class="code-content">
            <code>
              <span class="keyword">class</span>
              <span class="class-name">BackendDeveloper</span> {<br />
              &nbsp;&nbsp;<span class="keyword">constructor</span>() {<br />
              &nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword">this</span>.name =
              <span class="string">"Bevan"</span>;<br />
              &nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword">this</span>.role =
              <span class="string">"Backend Dev"</span>;<br />
              &nbsp;&nbsp;}<br />
              <br />
              &nbsp;&nbsp;<span class="function">build</span>() {<br />
              &nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword">return</span>
              <span class="string">"Model View Controller"</span>;<br />
              &nbsp;&nbsp;}<br />
              }
            </code>
          </div>
        </div>
      </div>
    </div>
    <div class="scroll-indicator">
      <span>Scroll Down</span>
      <div class="mouse">
        <div class="wheel"></div>
      </div>
    </div>
  </section>
</template>

<script setup></script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  padding: 8rem 2rem 4rem;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -50%;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, rgba(0, 255, 255, 0.1) 0%, transparent 70%);
  animation: pulse 8s ease-in-out infinite;
}

@keyframes pulse {
  0%,
  100% {
    opacity: 0.5;
    transform: scale(1);
  }
  50% {
    opacity: 0.8;
    transform: scale(1.1);
  }
}

.hero-content {
  max-width: 1200px;
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  position: relative;
  z-index: 1;
}

.text-content {
  animation: fadeInLeft 1s ease-out;
}

@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.greeting {
  font-size: 1.5rem;
  color: #00ffff;
  margin-bottom: 0.5rem;
  font-weight: 500;
}

.name {
  font-size: 4.5rem;
  font-weight: 800;
  margin: 0;
  background: linear-gradient(135deg, #fff, #00ffff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  line-height: 1.2;
}

.role {
  font-size: 2.5rem;
  color: #00ff88;
  margin: 0.5rem 0 1.5rem;
  font-weight: 600;
}

.tagline {
  font-size: 1.2rem;
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 2.5rem;
  line-height: 1.6;
}

.cta-buttons {
  display: flex;
  gap: 1.5rem;
}

.btn {
  padding: 1rem 2.5rem;
  border-radius: 50px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1rem;
  transition: all 0.3s ease;
  display: inline-block;
}

.btn-primary {
  background: linear-gradient(135deg, #00ffff, #00ff88);
  color: #0a0a0f;
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.4);
}

.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 5px 30px rgba(0, 255, 255, 0.6);
}

.btn-secondary {
  background: transparent;
  color: #00ffff;
  border: 2px solid #00ffff;
}

.btn-secondary:hover {
  background: rgba(0, 255, 255, 0.1);
  transform: translateY(-3px);
}

.hero-visual {
  animation: fadeInRight 1s ease-out;
}

@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translateX(50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.code-block {
  background: rgba(20, 20, 30, 0.8);
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
  border: 1px solid rgba(0, 255, 255, 0.2);
}

.code-header {
  background: rgba(30, 30, 40, 0.9);
  padding: 0.8rem 1rem;
  display: flex;
  gap: 0.5rem;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.dot.red {
  background: #ff5f56;
}
.dot.yellow {
  background: #ffbd2e;
}
.dot.green {
  background: #27c93f;
}

.code-content {
  padding: 2rem;
  font-family: 'Courier New', monospace;
  font-size: 1rem;
  line-height: 1.8;
}

.code-content code {
  color: #fff;
}

.keyword {
  color: #ff79c6;
}

.class-name {
  color: #50fa7b;
}

.string {
  color: #f1fa8c;
}

.function {
  color: #8be9fd;
}

.scroll-indicator {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  color: rgba(255, 255, 255, 0.5);
  font-size: 0.9rem;
  animation: bounce 2s infinite;
}

@keyframes bounce {
  0%,
  100% {
    transform: translateX(-50%) translateY(0);
  }
  50% {
    transform: translateX(-50%) translateY(-10px);
  }
}

.mouse {
  width: 25px;
  height: 40px;
  border: 2px solid rgba(0, 255, 255, 0.5);
  border-radius: 15px;
  position: relative;
}

.wheel {
  width: 3px;
  height: 8px;
  background: #00ffff;
  border-radius: 2px;
  position: absolute;
  top: 8px;
  left: 50%;
  transform: translateX(-50%);
  animation: scroll 2s infinite;
}

@keyframes scroll {
  0% {
    top: 8px;
    opacity: 1;
  }
  100% {
    top: 20px;
    opacity: 0;
  }
}

@media (max-width: 968px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .name {
    font-size: 3.5rem;
  }

  .role {
    font-size: 2rem;
  }

  .hero-visual {
    order: -1;
  }

  .code-block {
    max-width: 500px;
    margin: 0 auto;
  }
}

@media (max-width: 640px) {
  .hero {
    padding: 6rem 1.5rem 4rem;
  }

  .name {
    font-size: 2.5rem;
  }

  .role {
    font-size: 1.5rem;
  }

  .tagline {
    font-size: 1rem;
  }

  .cta-buttons {
    flex-direction: column;
    gap: 1rem;
  }

  .btn {
    text-align: center;
  }

  .code-content {
    font-size: 0.85rem;
    padding: 1.5rem;
  }
}
</style>
