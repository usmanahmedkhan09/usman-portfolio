<template>
  <section id="about" class="about section">
    <div class="container">
      <h2 class="section-title">About Me</h2>
      
      <div class="about-content">
        <div class="about-text">
          <div class="about-intro">
            <h3>Backend Software Engineer</h3>
            <p>
              I'm Usman Farooq, a dedicated backend software engineer with a strong foundation in 
              computer science and a passion for building robust, scalable web applications. 
              With 8 months of focused self-study in Vue.js and extensive experience in Python Django, 
              I specialize in creating efficient backend systems that power modern web applications.
            </p>
          </div>
          
          <div class="about-details">
            <div class="detail-item">
              <h4>🎯 Focus Areas</h4>
              <p>Backend Development, API Design, Database Architecture, Python Django Framework</p>
            </div>
            
            <div class="detail-item">
              <h4>💡 Philosophy</h4>
              <p>I believe in writing clean, maintainable code and following best practices to create solutions that scale and perform efficiently.</p>
            </div>
            
            <div class="detail-item">
              <h4>🚀 Goals</h4>
              <p>Seeking opportunities to contribute to innovative projects and grow as a backend developer while delivering high-quality software solutions.</p>
            </div>
          </div>
        </div>
        
        <div class="about-info">
          <div class="info-card">
            <h4>Personal Information</h4>
            <div class="info-list">
              <div class="info-item">
                <span class="label">Name:</span>
                <span class="value">Usman Farooq</span>
              </div>
              <div class="info-item">
                <span class="label">Email:</span>
                <span class="value">usmanf996@gmail.com</span>
              </div>
              <div class="info-item">
                <span class="label">Phone:</span>
                <span class="value">+44 743 846 7072</span>
              </div>
              <div class="info-item">
                <span class="label">Location:</span>
                <span class="value">United Kingdom</span>
              </div>
              <div class="info-item">
                <span class="label">Specialization:</span>
                <span class="value">Backend Development</span>
              </div>
              <div class="info-item">
                <span class="label">Experience:</span>
                <span class="value">8+ Months</span>
              </div>
            </div>
          </div>
          
          <div class="info-card">
            <h4>Technical Interests</h4>
            <div class="interests">
              <span class="interest-tag">Python Development</span>
              <span class="interest-tag">Django Framework</span>
              <span class="interest-tag">REST APIs</span>
              <span class="interest-tag">Database Design</span>
              <span class="interest-tag">Web Architecture</span>
              <span class="interest-tag">Vue.js</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Component logic can be added here if needed
</script>

<style scoped>
.about {
  background: white;
}

.about-content {
  display: grid;
  grid-template-columns: 1.5fr 1fr;
  gap: 4rem;
  align-items: start;
}

.about-text {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.about-intro h3 {
  font-size: 1.75rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 1rem;
}

.about-intro p {
  font-size: 1.1rem;
  line-height: 1.7;
  color: #64748b;
}

.about-details {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.detail-item h4 {
  font-size: 1.1rem;
  font-weight: 600;
  color: #1e293b;
  margin-bottom: 0.5rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.detail-item p {
  color: #64748b;
  line-height: 1.6;
}

.about-info {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.info-card {
  background: #f8fafc;
  border-radius: 15px;
  padding: 2rem;
  border: 1px solid #e2e8f0;
}

.info-card h4 {
  font-size: 1.25rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 1.5rem;
  text-align: center;
}

.info-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.info-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.75rem 0;
  border-bottom: 1px solid #e2e8f0;
}

.info-item:last-child {
  border-bottom: none;
}

.label {
  font-weight: 600;
  color: #475569;
  font-size: 0.9rem;
}

.value {
  color: #1e293b;
  font-weight: 500;
  text-align: right;
}

.interests {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.interest-tag {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 25px;
  font-size: 0.875rem;
  font-weight: 500;
  text-align: center;
}

@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .about-intro h3 {
    font-size: 1.5rem;
  }
  
  .info-item {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.25rem;
  }
  
  .value {
    text-align: left;
  }
  
  .interests {
    justify-content: center;
  }
}
</style>
