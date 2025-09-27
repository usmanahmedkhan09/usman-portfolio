<template>
  <section id="projects" class="projects section">
    <div class="container">
      <h2 class="section-title">Projects</h2>
      
      <div class="projects-content">
        <!-- Project Upload Section -->
        <div class="upload-section card">
          <div class="upload-header">
            <h3>Add New Project</h3>
            <p>Upload your projects to showcase your work</p>
          </div>
          
          <form @submit.prevent="addProject" class="upload-form">
            <div class="form-row">
              <div class="form-group">
                <label for="projectTitle">Project Title</label>
                <input 
                  type="text" 
                  id="projectTitle" 
                  v-model="newProject.title" 
                  placeholder="Enter project title"
                  required
                >
              </div>
              
              <div class="form-group">
                <label for="projectTech">Technology Stack</label>
                <input 
                  type="text" 
                  id="projectTech" 
                  v-model="newProject.tech" 
                  placeholder="e.g., Django, Vue.js, PostgreSQL"
                  required
                >
              </div>
            </div>
            
            <div class="form-group">
              <label for="projectDescription">Description</label>
              <textarea 
                id="projectDescription" 
                v-model="newProject.description" 
                placeholder="Describe your project..."
                rows="3"
                required
              ></textarea>
            </div>
            
            <div class="form-row">
              <div class="form-group">
                <label for="projectGithub">GitHub Repository</label>
                <input 
                  type="url" 
                  id="projectGithub" 
                  v-model="newProject.github" 
                  placeholder="https://github.com/username/repo"
                >
              </div>
              
              <div class="form-group">
                <label for="projectDemo">Live Demo URL</label>
                <input 
                  type="url" 
                  id="projectDemo" 
                  v-model="newProject.demo" 
                  placeholder="https://your-project-demo.com"
                >
              </div>
            </div>
            
            <div class="form-group">
              <label for="projectImage">Project Image</label>
              <div class="file-upload">
                <input 
                  type="file" 
                  id="projectImage" 
                  @change="handleImageUpload" 
                  accept="image/*"
                  ref="fileInput"
                >
                <label for="projectImage" class="file-upload-label">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
                    <circle cx="8.5" cy="8.5" r="1.5"></circle>
                    <polyline points="21,15 16,10 5,21"></polyline>
                  </svg>
                  Choose Image
                </label>
                <span class="file-name" v-if="newProject.imageName">{{ newProject.imageName }}</span>
              </div>
            </div>
            
            <button type="submit" class="btn" :disabled="isUploading">
              <span v-if="isUploading">Adding Project...</span>
              <span v-else>Add Project</span>
            </button>
          </form>
        </div>

        <!-- Projects Grid -->
        <div class="projects-grid">
          <div class="project-card card" v-for="project in projects" :key="project.id">
            <div class="project-image">
              <img v-if="project.image" :src="project.image" :alt="project.title">
              <div v-else class="image-placeholder">
                <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                  <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
                  <circle cx="8.5" cy="8.5" r="1.5"></circle>
                  <polyline points="21,15 16,10 5,21"></polyline>
                </svg>
              </div>
              <div class="project-overlay">
                <div class="project-links">
                  <a v-if="project.github" :href="project.github" target="_blank" class="project-link">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                      <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                    </svg>
                  </a>
                  <a v-if="project.demo" :href="project.demo" target="_blank" class="project-link">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                      <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
                      <polyline points="15,3 21,3 21,9"></polyline>
                      <line x1="10" y1="14" x2="21" y2="3"></line>
                    </svg>
                  </a>
                </div>
              </div>
            </div>
            
            <div class="project-content">
              <h3 class="project-title">{{ project.title }}</h3>
              <p class="project-description">{{ project.description }}</p>
              
              <div class="project-tech">
                <span v-for="tech in project.techArray" :key="tech" class="tech-tag">
                  {{ tech }}
                </span>
              </div>
              
              <div class="project-actions">
                <button @click="deleteProject(project.id)" class="delete-btn">
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <polyline points="3,6 5,6 21,6"></polyline>
                    <path d="m19,6v14a2,2 0 0,1 -2,2H7a2,2 0 0,1 -2,-2V6m3,0V4a2,2 0 0,1 2,-2h4a2,2 0 0,1 2,2v2"></path>
                  </svg>
                  Delete
                </button>
              </div>
            </div>
          </div>
          
          <!-- Empty State -->
          <div v-if="projects.length === 0" class="empty-state">
            <div class="empty-icon">
              <svg width="60" height="60" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                <rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect>
                <line x1="16" y1="2" x2="16" y2="6"></line>
                <line x1="8" y1="2" x2="8" y2="6"></line>
                <line x1="3" y1="10" x2="21" y2="10"></line>
              </svg>
            </div>
            <h3>No Projects Yet</h3>
            <p>Start by adding your first project using the form above.</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue'

const projects = ref([])
const isUploading = ref(false)
const fileInput = ref(null)

const newProject = reactive({
  title: '',
  description: '',
  tech: '',
  github: '',
  demo: '',
  image: null,
  imageName: ''
})

const handleImageUpload = (event) => {
  const file = event.target.files[0]
  if (file) {
    newProject.imageName = file.name
    const reader = new FileReader()
    reader.onload = (e) => {
      newProject.image = e.target.result
    }
    reader.readAsDataURL(file)
  }
}

const addProject = () => {
  isUploading.value = true
  
  // Simulate upload delay
  setTimeout(() => {
    const project = {
      id: Date.now(),
      title: newProject.title,
      description: newProject.description,
      tech: newProject.tech,
      techArray: newProject.tech.split(',').map(t => t.trim()),
      github: newProject.github,
      demo: newProject.demo,
      image: newProject.image,
      createdAt: new Date().toLocaleDateString()
    }
    
    projects.value.unshift(project)
    
    // Reset form
    Object.keys(newProject).forEach(key => {
      newProject[key] = ''
    })
    newProject.image = null
    
    if (fileInput.value) {
      fileInput.value.value = ''
    }
    
    isUploading.value = false
  }, 1000)
}

const deleteProject = (id) => {
  if (confirm('Are you sure you want to delete this project?')) {
    projects.value = projects.value.filter(project => project.id !== id)
  }
}
</script>

<style scoped>
.projects {
  background: #f8fafc;
}

.projects-content {
  display: flex;
  flex-direction: column;
  gap: 3rem;
}

.upload-section {
  background: white;
  padding: 2rem;
}

.upload-header {
  text-align: center;
  margin-bottom: 2rem;
}

.upload-header h3 {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 0.5rem;
}

.upload-header p {
  color: #64748b;
}

.upload-form {
  max-width: 600px;
  margin: 0 auto;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  font-weight: 600;
  color: #374151;
  margin-bottom: 0.5rem;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
}

.file-upload {
  position: relative;
  display: flex;
  align-items: center;
  gap: 1rem;
}

.file-upload input[type="file"] {
  position: absolute;
  opacity: 0;
  width: 0;
  height: 0;
}

.file-upload-label {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1rem;
  background: #f8fafc;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-weight: 500;
  color: #374151;
}

.file-upload-label:hover {
  background: #e2e8f0;
  border-color: #667eea;
}

.file-name {
  color: #64748b;
  font-size: 0.9rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.project-card {
  background: white;
  overflow: hidden;
  transition: all 0.3s ease;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
}

.project-image {
  position: relative;
  height: 200px;
  overflow: hidden;
  background: #f8fafc;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.image-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #94a3b8;
  background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-image:hover .project-overlay {
  opacity: 1;
}

.project-links {
  display: flex;
  gap: 1rem;
}

.project-link {
  width: 40px;
  height: 40px;
  background: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #374151;
  text-decoration: none;
  transition: all 0.3s ease;
}

.project-link:hover {
  background: #667eea;
  color: white;
  transform: scale(1.1);
}

.project-content {
  padding: 1.5rem;
}

.project-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 0.75rem;
}

.project-description {
  color: #64748b;
  line-height: 1.6;
  margin-bottom: 1rem;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.tech-tag {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 0.25rem 0.75rem;
  border-radius: 15px;
  font-size: 0.8rem;
  font-weight: 500;
}

.project-actions {
  display: flex;
  justify-content: flex-end;
}

.delete-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  background: #fee2e2;
  color: #dc2626;
  border: 1px solid #fecaca;
  border-radius: 6px;
  cursor: pointer;
  font-size: 0.875rem;
  transition: all 0.3s ease;
}

.delete-btn:hover {
  background: #fecaca;
  border-color: #f87171;
}

.empty-state {
  grid-column: 1 / -1;
  text-align: center;
  padding: 3rem;
  color: #64748b;
}

.empty-icon {
  margin-bottom: 1rem;
  color: #94a3b8;
}

.empty-state h3 {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: #374151;
}

@media (max-width: 768px) {
  .form-row {
    grid-template-columns: 1fr;
  }
  
  .projects-grid {
    grid-template-columns: 1fr;
  }
  
  .file-upload {
    flex-direction: column;
    align-items: stretch;
  }
}
</style>
