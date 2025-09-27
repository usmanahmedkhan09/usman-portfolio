<template>
  <header class="header">
    <nav class="nav container">
      <div class="nav-brand">
        <h2 class="text-gradient">Usman Farooq</h2>
      </div>
      
      <ul class="nav-menu" :class="{ active: isMenuOpen }">
        <li><a href="#home" @click="closeMenu">Home</a></li>
        <li><a href="#about" @click="closeMenu">About</a></li>
        <li><a href="#education" @click="closeMenu">Education</a></li>
        <li><a href="#skills" @click="closeMenu">Skills</a></li>
        <li><a href="#projects" @click="closeMenu">Projects</a></li>
        <li><a href="#contact" @click="closeMenu">Contact</a></li>
      </ul>
      
      <div class="nav-contact">
        <a href="tel:+447438467072" class="contact-link">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
            <path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/>
          </svg>
          +44 743 846 7072
        </a>
      </div>
      
      <div class="nav-toggle" @click="toggleMenu">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid #e2e8f0;
  z-index: 1000;
  transition: all 0.3s ease;
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 0;
  min-height: 80px;
}

.nav-brand h2 {
  font-size: 1.5rem;
  font-weight: 700;
}

.nav-menu {
  display: flex;
  list-style: none;
  gap: 2rem;
  margin: 0;
}

.nav-menu li a {
  text-decoration: none;
  color: #64748b;
  font-weight: 500;
  transition: color 0.3s ease;
  position: relative;
}

.nav-menu li a:hover {
  color: #667eea;
}

.nav-menu li a::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  transition: width 0.3s ease;
}

.nav-menu li a:hover::after {
  width: 100%;
}

.nav-contact {
  display: flex;
  align-items: center;
}

.contact-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #64748b;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.contact-link:hover {
  color: #667eea;
}

.nav-toggle {
  display: none;
  flex-direction: column;
  cursor: pointer;
  gap: 4px;
}

.nav-toggle span {
  width: 25px;
  height: 3px;
  background: #64748b;
  transition: all 0.3s ease;
  border-radius: 2px;
}

@media (max-width: 768px) {
  .nav-menu {
    position: fixed;
    top: 80px;
    left: 0;
    right: 0;
    background: rgba(255, 255, 255, 0.98);
    backdrop-filter: blur(10px);
    flex-direction: column;
    padding: 2rem;
    transform: translateX(-100%);
    transition: transform 0.3s ease;
    border-bottom: 1px solid #e2e8f0;
  }

  .nav-menu.active {
    transform: translateX(0);
  }

  .nav-contact {
    display: none;
  }

  .nav-toggle {
    display: flex;
  }

  .nav-toggle.active span:nth-child(1) {
    transform: rotate(45deg) translate(5px, 5px);
  }

  .nav-toggle.active span:nth-child(2) {
    opacity: 0;
  }

  .nav-toggle.active span:nth-child(3) {
    transform: rotate(-45deg) translate(7px, -6px);
  }
}
</style>
