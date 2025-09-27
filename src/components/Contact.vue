<template>
  <section id="contact" class="contact section">
    <div class="container">
      <h2 class="section-title">Get In Touch</h2>
      
      <div class="contact-content">
        <div class="contact-info">
          <div class="contact-intro">
            <h3>Let's Work Together</h3>
            <p>
              I'm always interested in new opportunities and exciting projects. 
              Whether you have a project in mind or just want to connect, feel free to reach out!
            </p>
          </div>
          
          <div class="contact-methods">
            <div class="contact-method">
              <div class="method-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
                </svg>
              </div>
              <div class="method-info">
                <h4>Email</h4>
                <a href="mailto:usmanf996@gmail.com">usmanf996@gmail.com</a>
              </div>
            </div>
            
            <div class="contact-method">
              <div class="method-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/>
                </svg>
              </div>
              <div class="method-info">
                <h4>Phone</h4>
                <a href="tel:+447438467072">+44 743 846 7072</a>
              </div>
            </div>
            
            <div class="contact-method">
              <div class="method-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
                </svg>
              </div>
              <div class="method-info">
                <h4>Location</h4>
                <span>United Kingdom</span>
              </div>
            </div>
          </div>
          
          <div class="availability">
            <h4>🟢 Available for Work</h4>
            <p>Currently seeking backend developer opportunities</p>
          </div>
        </div>
        
        <div class="contact-form-container">
          <form @submit.prevent="sendMessage" class="contact-form card">
            <div class="form-header">
              <h3>Send a Message</h3>
              <p>I'll get back to you as soon as possible</p>
            </div>
            
            <div class="form-group">
              <label for="name">Your Name</label>
              <input 
                type="text" 
                id="name" 
                v-model="form.name" 
                placeholder="Enter your name"
                required
              >
            </div>
            
            <div class="form-group">
              <label for="email">Your Email</label>
              <input 
                type="email" 
                id="email" 
                v-model="form.email" 
                placeholder="Enter your email"
                required
              >
            </div>
            
            <div class="form-group">
              <label for="subject">Subject</label>
              <select id="subject" v-model="form.subject" required>
                <option value="">Select a subject</option>
                <option value="job-opportunity">Job Opportunity</option>
                <option value="project-collaboration">Project Collaboration</option>
                <option value="freelance-work">Freelance Work</option>
                <option value="general-inquiry">General Inquiry</option>
                <option value="other">Other</option>
              </select>
            </div>
            
            <div class="form-group">
              <label for="message">Message</label>
              <textarea 
                id="message" 
                v-model="form.message" 
                placeholder="Tell me about your project or opportunity..."
                rows="5"
                required
              ></textarea>
            </div>
            
            <button type="submit" class="btn btn-full" :disabled="isSubmitting">
              <span v-if="isSubmitting">Sending...</span>
              <span v-else>Send Message</span>
            </button>
            
            <div v-if="submitMessage" class="submit-message" :class="submitMessageType">
              {{ submitMessage }}
            </div>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue'

const isSubmitting = ref(false)
const submitMessage = ref('')
const submitMessageType = ref('')

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const sendMessage = async () => {
  isSubmitting.value = true
  submitMessage.value = ''
  
  try {
    // Simulate form submission
    await new Promise(resolve => setTimeout(resolve, 2000))
    
    // In a real application, you would send the form data to your backend
    console.log('Form submitted:', form)
    
    submitMessage.value = 'Thank you for your message! I\'ll get back to you soon.'
    submitMessageType.value = 'success'
    
    // Reset form
    Object.keys(form).forEach(key => {
      form[key] = ''
    })
    
  } catch (error) {
    submitMessage.value = 'Sorry, there was an error sending your message. Please try again.'
    submitMessageType.value = 'error'
  } finally {
    isSubmitting.value = false
    
    // Clear message after 5 seconds
    setTimeout(() => {
      submitMessage.value = ''
    }, 5000)
  }
}
</script>

<style scoped>
.contact {
  background: white;
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.contact-intro h3 {
  font-size: 1.75rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 1rem;
}

.contact-intro p {
  font-size: 1.1rem;
  line-height: 1.7;
  color: #64748b;
}

.contact-methods {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.contact-method {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  background: #f8fafc;
  border-radius: 12px;
  border: 1px solid #e2e8f0;
  transition: all 0.3s ease;
}

.contact-method:hover {
  background: white;
  border-color: #667eea;
  transform: translateX(5px);
}

.method-icon {
  width: 50px;
  height: 50px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  flex-shrink: 0;
}

.method-info h4 {
  font-size: 1rem;
  font-weight: 600;
  color: #1e293b;
  margin-bottom: 0.25rem;
}

.method-info a {
  color: #667eea;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.method-info a:hover {
  color: #764ba2;
}

.method-info span {
  color: #64748b;
  font-weight: 500;
}

.availability {
  background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 100%);
  border: 1px solid #bbf7d0;
  border-radius: 12px;
  padding: 1.5rem;
  text-align: center;
}

.availability h4 {
  font-size: 1.1rem;
  font-weight: 600;
  color: #15803d;
  margin-bottom: 0.5rem;
}

.availability p {
  color: #166534;
  font-weight: 500;
}

.contact-form-container {
  position: sticky;
  top: 100px;
}

.contact-form {
  background: white;
  padding: 2rem;
}

.form-header {
  text-align: center;
  margin-bottom: 2rem;
}

.form-header h3 {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 0.5rem;
}

.form-header p {
  color: #64748b;
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
.form-group select,
.form-group textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
  font-family: inherit;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.btn-full {
  width: 100%;
  padding: 1rem;
  font-size: 1.1rem;
}

.btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.submit-message {
  margin-top: 1rem;
  padding: 0.75rem;
  border-radius: 8px;
  text-align: center;
  font-weight: 500;
}

.submit-message.success {
  background: #f0fdf4;
  color: #15803d;
  border: 1px solid #bbf7d0;
}

.submit-message.error {
  background: #fef2f2;
  color: #dc2626;
  border: 1px solid #fecaca;
}

@media (max-width: 768px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .contact-form-container {
    position: static;
  }
  
  .contact-intro h3 {
    font-size: 1.5rem;
  }
  
  .method-icon {
    width: 40px;
    height: 40px;
  }
}
</style>
