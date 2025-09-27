<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-main">
          <div class="footer-brand">
            <h3 class="text-gradient">Usman Farooq</h3>
            <p>Backend Software Engineer</p>
            <p class="footer-description">
              Building robust and scalable backend systems with Python Django. 
              Passionate about clean code and innovative solutions.
            </p>
          </div>
          
          <div class="footer-links">
            <div class="link-group">
              <h4>Navigation</h4>
              <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#education">Education</a></li>
                <li><a href="#skills">Skills</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#contact">Contact</a></li>
              </ul>
            </div>
            
            <div class="link-group">
              <h4>Technologies</h4>
              <ul>
                <li>Python</li>
                <li>Django</li>
                <li>Vue.js</li>
                <li>PostgreSQL</li>
                <li>REST APIs</li>
                <li>Git & GitHub</li>
              </ul>
            </div>
            
            <div class="link-group">
              <h4>Connect</h4>
              <ul>
                <li><a href="mailto:usmanf996@gmail.com">Email</a></li>
                <li><a href="tel:+447438467072">Phone</a></li>
                <li><a href="#" target="_blank">LinkedIn</a></li>
                <li><a href="#" target="_blank">GitHub</a></li>
              </ul>
            </div>
          </div>
        </div>
        
        <div class="footer-bottom">
          <div class="footer-info">
            <p>&copy; {{ currentYear }} Usman Farooq. All rights reserved.</p>
            <p>Built with Vue.js & ❤️</p>
          </div>
          
          <div class="footer-social">
            <a href="#" class="social-link" title="GitHub">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
              </svg>
            </a>
            
            <a href="#" class="social-link" title="LinkedIn">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
              </svg>
            </a>
            
            <a href="mailto:usmanf996@gmail.com" class="social-link" title="Email">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue';

const currentYear = computed(() => new Date().getFullYear())
</script>

<style scoped>
.footer {
  background: linear-gradient(135deg, #1e293b 0%, #334155 100%);
  color: white;
  padding: 3rem 0 1rem;
}

.footer-content {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.footer-main {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 3rem;
  align-items: start;
}

.footer-brand h3 {
  font-size: 1.75rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.footer-brand > p {
  color: #94a3b8;
  font-weight: 500;
  margin-bottom: 1rem;
}

.footer-description {
  color: #cbd5e1;
  line-height: 1.6;
  max-width: 300px;
}

.footer-links {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.link-group h4 {
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: white;
}

.link-group ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.link-group li {
  margin-bottom: 0.5rem;
}

.link-group a {
  color: #94a3b8;
  text-decoration: none;
  transition: color 0.3s ease;
  font-weight: 400;
}

.link-group a:hover {
  color: white;
}

.link-group li:not(:has(a)) {
  color: #94a3b8;
  font-weight: 400;
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 2rem;
  border-top: 1px solid #475569;
}

.footer-info p {
  color: #94a3b8;
  font-size: 0.9rem;
  margin: 0;
}

.footer-info p:first-child {
  margin-bottom: 0.25rem;
}

.footer-social {
  display: flex;
  gap: 1rem;
}

.social-link {
  width: 40px;
  height: 40px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #94a3b8;
  text-decoration: none;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.social-link:hover {
  background: rgba(255, 255, 255, 0.2);
  color: white;
  transform: translateY(-2px);
}

@media (max-width: 768px) {
  .footer {
    padding: 2rem 0 1rem;
  }
  
  .footer-main {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .footer-links {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
  
  .footer-bottom {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
  }
  
  .footer-brand h3 {
    font-size: 1.5rem;
  }
  
  .footer-description {
    max-width: none;
  }
}

@media (max-width: 480px) {
  .footer-links {
    grid-template-columns: 1fr;
  }
  
  .footer-social {
    justify-content: center;
  }
}
</style>
