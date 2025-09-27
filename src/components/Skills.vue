<template>
  <section id="skills" class="skills section">
    <div class="container">
      <h2 class="section-title">Skills & Technologies</h2>
      
      <div class="skills-content">
        <!-- Primary Skills -->
        <div class="skills-category">
          <h3 class="category-title">
            <span class="icon">🚀</span>
            Primary Backend Technologies
          </h3>
          <div class="skills-grid">
            <div class="skill-card card" v-for="skill in primarySkills" :key="skill.name">
              <div class="skill-icon">
                <div class="icon-bg" :style="{ background: skill.color }">
                  <span v-html="skill.icon"></span>
                </div>
              </div>
              <div class="skill-info">
                <h4 class="skill-name">{{ skill.name }}</h4>
                <p class="skill-description">{{ skill.description }}</p>
                <div class="skill-level">
                  <div class="level-bar">
                    <div class="level-fill" :style="{ width: skill.level + '%', background: skill.color }"></div>
                  </div>
                  <span class="level-text">{{ skill.experience }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Frontend Skills -->
        <div class="skills-category">
          <h3 class="category-title">
            <span class="icon">💻</span>
            Frontend Development
          </h3>
          <div class="skills-grid">
            <div class="skill-card card" v-for="skill in frontendSkills" :key="skill.name">
              <div class="skill-icon">
                <div class="icon-bg" :style="{ background: skill.color }">
                  <span v-html="skill.icon"></span>
                </div>
              </div>
              <div class="skill-info">
                <h4 class="skill-name">{{ skill.name }}</h4>
                <p class="skill-description">{{ skill.description }}</p>
                <div class="skill-level">
                  <div class="level-bar">
                    <div class="level-fill" :style="{ width: skill.level + '%', background: skill.color }"></div>
                  </div>
                  <span class="level-text">{{ skill.experience }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Tools & Technologies -->
        <div class="skills-category">
          <h3 class="category-title">
            <span class="icon">🛠️</span>
            Tools & Technologies
          </h3>
          <div class="tools-grid">
            <div class="tool-item" v-for="tool in tools" :key="tool.name">
              <div class="tool-icon" v-html="tool.icon"></div>
              <span class="tool-name">{{ tool.name }}</span>
            </div>
          </div>
        </div>

        <!-- Learning Path -->
        <div class="learning-section">
          <h3 class="category-title">
            <span class="icon">📚</span>
            Currently Learning & Expanding
          </h3>
          <div class="learning-items">
            <div class="learning-item" v-for="item in learningPath" :key="item">
              <span class="learning-bullet">▸</span>
              <span>{{ item }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const primarySkills = ref([
  {
    name: 'Python',
    description: 'Primary programming language for backend development',
    level: 85,
    experience: '8+ Months',
    color: 'linear-gradient(135deg, #3776ab 0%, #ffd43b 100%)',
    icon: '🐍'
  },
  {
    name: 'Django',
    description: 'Main framework for building robust web applications',
    level: 80,
    experience: '8+ Months',
    color: 'linear-gradient(135deg, #092e20 0%, #44b78b 100%)',
    icon: '🎯'
  },
  {
    name: 'REST APIs',
    description: 'Designing and implementing RESTful web services',
    level: 75,
    experience: '6+ Months',
    color: 'linear-gradient(135deg, #ff6b6b 0%, #feca57 100%)',
    icon: '🔗'
  },
  {
    name: 'Database Design',
    description: 'PostgreSQL, MySQL, and database architecture',
    level: 70,
    experience: '6+ Months',
    color: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)',
    icon: '🗄️'
  }
])

const frontendSkills = ref([
  {
    name: 'Vue.js',
    description: 'Progressive JavaScript framework for building user interfaces',
    level: 70,
    experience: '8+ Months',
    color: 'linear-gradient(135deg, #4fc08d 0%, #42b883 100%)',
    icon: '⚡'
  },
  {
    name: 'HTML5 & CSS3',
    description: 'Modern web markup and styling technologies',
    level: 75,
    experience: '8+ Months',
    color: 'linear-gradient(135deg, #e34c26 0%, #1572b6 100%)',
    icon: '🎨'
  },
  {
    name: 'JavaScript',
    description: 'Core JavaScript for interactive web applications',
    level: 65,
    experience: '6+ Months',
    color: 'linear-gradient(135deg, #f7df1e 0%, #ffb400 100%)',
    icon: '⚙️'
  }
])

const tools = ref([
  { name: 'Git & GitHub', icon: '📦' },
  { name: 'VS Code', icon: '💻' },
  { name: 'PostgreSQL', icon: '🐘' },
  { name: 'MySQL', icon: '🗃️' },
  { name: 'Postman', icon: '📡' },
  { name: 'Linux/Ubuntu', icon: '🐧' },
  { name: 'Docker', icon: '🐳' },
  { name: 'Vite', icon: '⚡' }
])

const learningPath = ref([
  'Advanced Django Features (Celery, Redis, Caching)',
  'Django REST Framework for API Development',
  'Cloud Deployment (AWS, Heroku, DigitalOcean)',
  'Testing Frameworks (pytest, Django Testing)',
  'Microservices Architecture',
  'GraphQL with Django',
  'DevOps and CI/CD Pipelines'
])
</script>

<style scoped>
.skills {
  background: white;
}

.skills-content {
  display: flex;
  flex-direction: column;
  gap: 4rem;
}

.skills-category {
  margin-bottom: 2rem;
}

.category-title {
  font-size: 1.75rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 2rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.category-title .icon {
  font-size: 2rem;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.skill-card {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  padding: 1.5rem;
  transition: all 0.3s ease;
}

.skill-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
}

.skill-icon {
  flex-shrink: 0;
}

.icon-bg {
  width: 50px;
  height: 50px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  color: white;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.skill-info {
  flex: 1;
}

.skill-name {
  font-size: 1.1rem;
  font-weight: 600;
  color: #1e293b;
  margin-bottom: 0.5rem;
}

.skill-description {
  color: #64748b;
  font-size: 0.9rem;
  margin-bottom: 1rem;
  line-height: 1.5;
}

.skill-level {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.level-bar {
  flex: 1;
  height: 6px;
  background: #e2e8f0;
  border-radius: 3px;
  overflow: hidden;
}

.level-fill {
  height: 100%;
  border-radius: 3px;
  transition: width 0.8s ease;
}

.level-text {
  font-size: 0.8rem;
  font-weight: 600;
  color: #64748b;
  white-space: nowrap;
}

.tools-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1rem;
}

.tool-item {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1rem;
  text-align: center;
  transition: all 0.3s ease;
  cursor: pointer;
}

.tool-item:hover {
  background: white;
  border-color: #667eea;
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(102, 126, 234, 0.1);
}

.tool-icon {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

.tool-name {
  font-size: 0.9rem;
  font-weight: 500;
  color: #475569;
}

.learning-section {
  background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
  border-radius: 20px;
  padding: 2rem;
  border: 1px solid #e2e8f0;
}

.learning-items {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}

.learning-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem;
  background: white;
  border-radius: 10px;
  border: 1px solid #e2e8f0;
  transition: all 0.3s ease;
}

.learning-item:hover {
  border-color: #667eea;
  transform: translateX(5px);
}

.learning-bullet {
  color: #667eea;
  font-weight: bold;
  font-size: 1.1rem;
}

@media (max-width: 768px) {
  .skills-grid {
    grid-template-columns: 1fr;
  }
  
  .tools-grid {
    grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  }
  
  .learning-items {
    grid-template-columns: 1fr;
  }
  
  .skill-level {
    flex-direction: column;
    align-items: stretch;
    gap: 0.5rem;
  }
  
  .level-text {
    text-align: center;
  }
  
  .category-title {
    font-size: 1.5rem;
  }
}
</style>
