<template>
  <section id="home" class="hero section">
    <div class="container">
      <div class="hero-content">
        <div class="hero-text">
          <h1 class="hero-title">
            Hi, I'm <span class="text-gradient">Usman Farooq</span>
          </h1>
          <h2 class="hero-subtitle">Backend Software Engineer</h2>
          <p class="hero-description">
            Passionate about building robust and scalable backend systems with Python Django. 
            Currently expanding my expertise in web development and seeking opportunities to 
            contribute to innovative projects as a backend developer.
          </p>
          <div class="hero-buttons">
            <a href="#contact" class="btn">Get In Touch</a>
            <a href="#projects" class="btn btn-outline">View Projects</a>
          </div>
          <div class="hero-stats">
            <div class="stat">
              <span class="stat-number">8+</span>
              <span class="stat-label">Months Experience</span>
            </div>
            <div class="stat">
              <span class="stat-number">Python</span>
              <span class="stat-label">Primary Language</span>
            </div>
            <div class="stat">
              <span class="stat-number">Django</span>
              <span class="stat-label">Main Framework</span>
            </div>
          </div>
        </div>
        <div class="hero-image">
          <div class="profile-image">
            <img src="/pic.jpg" alt="Usman Farooq - Backend Software Engineer" />
          </div>
        </div>
      </div>
    </div>
    
    <!-- Animated background elements -->
    <div class="hero-bg">
      <div class="bg-element bg-element-1"></div>
      <div class="bg-element bg-element-2"></div>
      <div class="bg-element bg-element-3"></div>
    </div>
  </section>
</template>

<script setup>
// Component logic can be added here if needed
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  position: relative;
  z-index: 2;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 1rem;
  color: #1e293b;
}

.hero-subtitle {
  font-size: 1.5rem;
  font-weight: 600;
  color: #64748b;
  margin-bottom: 1.5rem;
}

.hero-description {
  font-size: 1.1rem;
  color: #64748b;
  margin-bottom: 2.5rem;
  line-height: 1.7;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  margin-bottom: 3rem;
}

.hero-stats {
  display: flex;
  gap: 2rem;
}

.stat {
  text-align: center;
}

.stat-number {
  display: block;
  font-size: 1.5rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 0.25rem;
}

.stat-label {
  font-size: 0.875rem;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.hero-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.profile-image {
  width: 300px;
  height: 300px;
  border-radius: 50%;
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
  border: 4px solid #e2e8f0;
  position: relative;
  overflow: hidden;
}

.profile-image::before {
  content: '';
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 50%;
  z-index: -1;
}

.profile-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
  transition: transform 0.3s ease;
}

.profile-image:hover img {
  transform: scale(1.05);
}

/* Animated background elements */
.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1;
  overflow: hidden;
}

.bg-element {
  position: absolute;
  border-radius: 50%;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
  animation: float 6s ease-in-out infinite;
}

.bg-element-1 {
  width: 200px;
  height: 200px;
  top: 10%;
  right: 10%;
  animation-delay: 0s;
}

.bg-element-2 {
  width: 150px;
  height: 150px;
  bottom: 20%;
  left: 10%;
  animation-delay: 2s;
}

.bg-element-3 {
  width: 100px;
  height: 100px;
  top: 50%;
  right: 30%;
  animation-delay: 4s;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px) rotate(0deg);
  }
  50% {
    transform: translateY(-20px) rotate(180deg);
  }
}

@media (max-width: 768px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }

  .hero-title {
    font-size: 2.5rem;
  }

  .hero-subtitle {
    font-size: 1.25rem;
  }

  .hero-buttons {
    justify-content: center;
    flex-wrap: wrap;
  }

  .hero-stats {
    justify-content: center;
  }

  .profile-image {
    width: 250px;
    height: 250px;
  }

  .bg-element {
    display: none;
  }
}

@media (max-width: 480px) {
  .hero-stats {
    flex-direction: column;
    gap: 1rem;
  }

  .hero-buttons {
    flex-direction: column;
    align-items: center;
  }
}
</style>
