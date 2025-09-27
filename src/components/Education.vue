<template>
  <section id="education" class="education section">
    <div class="container">
      <h2 class="section-title">Education</h2>
      
      <div class="education-timeline">
        <div class="timeline-item" v-for="(edu, index) in education" :key="index">
          <div class="timeline-marker">
            <div class="marker-icon">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 3L1 9l4 2.18v6L12 21l7-3.82v-6l2-1.09V17h2V9L12 3zm6.82 6L12 12.72 5.18 9 12 5.28 18.82 9zM17 15.99l-5 2.73-5-2.73v-3.72L12 15l5-2.73v3.72z"/>
              </svg>
            </div>
          </div>
          
          <div class="timeline-content">
            <div class="education-card card">
              <div class="education-header">
                <h3 class="degree">{{ edu.degree }}</h3>
                <span class="duration">{{ edu.duration }}</span>
              </div>
              
              <div class="education-details">
                <h4 class="field">{{ edu.field }}</h4>
                <div class="institution">
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
                    <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
                  </svg>
                  <span>{{ edu.institution }}</span>
                </div>
                <div class="location">
                  <span>{{ edu.location }}</span>
                </div>
              </div>
              
              <div class="education-description" v-if="edu.description">
                <p>{{ edu.description }}</p>
              </div>
              
              <div class="education-highlights" v-if="edu.highlights">
                <h5>Key Highlights:</h5>
                <ul>
                  <li v-for="highlight in edu.highlights" :key="highlight">{{ highlight }}</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const education = ref([
  {
    degree: "Master of Science",
    field: "Computer Science",
    institution: "University of Bedfordshire",
    location: "Luton, United Kingdom",
    duration: "2023 - 2024",
    description: "Advanced studies in computer science with focus on software engineering, algorithms, and system design.",
    highlights: [
      "Advanced Software Engineering Principles",
      "Database Systems and Architecture", 
      "Web Technologies and Frameworks",
      "Research in Backend Development"
    ]
  },
  {
    degree: "Bachelor of Science",
    field: "Computer Science",
    institution: "COMSATS University of Science and Technology",
    location: "Abbottabad Campus, Pakistan",
    duration: "2019 - 2023",
    description: "Comprehensive undergraduate program covering fundamental computer science concepts, programming, and software development.",
    highlights: [
      "Programming Fundamentals (Python, Java, C++)",
      "Data Structures and Algorithms",
      "Software Engineering Methodologies",
      "Database Management Systems",
      "Web Development Technologies"
    ]
  }
])
</script>

<style scoped>
.education {
  background: #f8fafc;
}

.education-timeline {
  position: relative;
  max-width: 800px;
  margin: 0 auto;
}

.education-timeline::before {
  content: '';
  position: absolute;
  left: 30px;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.timeline-item {
  position: relative;
  margin-bottom: 3rem;
  padding-left: 80px;
}

.timeline-marker {
  position: absolute;
  left: 0;
  top: 0;
}

.marker-icon {
  width: 60px;
  height: 60px;
  background: white;
  border: 3px solid #667eea;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #667eea;
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.2);
}

.timeline-content {
  width: 100%;
}

.education-card {
  position: relative;
  background: white;
  transition: all 0.3s ease;
}

.education-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
}

.education-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 1rem;
  flex-wrap: wrap;
  gap: 1rem;
}

.degree {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1e293b;
  margin: 0;
}

.duration {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 25px;
  font-size: 0.875rem;
  font-weight: 600;
  white-space: nowrap;
}

.education-details {
  margin-bottom: 1.5rem;
}

.field {
  font-size: 1.25rem;
  font-weight: 600;
  color: #475569;
  margin-bottom: 1rem;
}

.institution {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #64748b;
  font-weight: 500;
  margin-bottom: 0.5rem;
}

.institution svg {
  color: #667eea;
}

.location {
  color: #94a3b8;
  font-size: 0.9rem;
  margin-left: 1.5rem;
}

.education-description {
  margin-bottom: 1.5rem;
}

.education-description p {
  color: #64748b;
  line-height: 1.6;
}

.education-highlights h5 {
  font-size: 1rem;
  font-weight: 600;
  color: #1e293b;
  margin-bottom: 0.75rem;
}

.education-highlights ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.education-highlights li {
  position: relative;
  padding-left: 1.5rem;
  margin-bottom: 0.5rem;
  color: #64748b;
  line-height: 1.5;
}

.education-highlights li::before {
  content: '▸';
  position: absolute;
  left: 0;
  color: #667eea;
  font-weight: bold;
}

@media (max-width: 768px) {
  .education-timeline::before {
    left: 20px;
  }
  
  .timeline-item {
    padding-left: 60px;
  }
  
  .marker-icon {
    width: 40px;
    height: 40px;
  }
  
  .education-header {
    flex-direction: column;
    align-items: flex-start;
  }
  
  .degree {
    font-size: 1.25rem;
  }
  
  .field {
    font-size: 1.1rem;
  }
}

@media (max-width: 480px) {
  .timeline-item {
    padding-left: 50px;
  }
  
  .education-timeline::before {
    left: 15px;
  }
  
  .marker-icon {
    width: 30px;
    height: 30px;
  }
}
</style>
