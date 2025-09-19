<template>
  <div class="modal-overlay" @click="closeModal">
    <div class="modal-content" @click.stop>
      <button class="modal-close" @click="closeModal">
        <i class="fas fa-times"></i>
      </button>
      
      <div class="modal-header">
        <img :src="project.image" :alt="project.title" class="modal-image" />
        <div class="modal-info">
          <div class="project-meta">
            <span class="project-category">{{ project.category }}</span>
            <span :class="['project-status', project.status]">
              {{ getStatusText(project.status) }}
            </span>
          </div>
          <h2>{{ project.title }}</h2>
        </div>
      </div>
      
      <div class="modal-body">
        <div class="description-section">
          <h3>Descripción del Proyecto</h3>
          <p>{{ project.longDescription }}</p>
        </div>
        
        <div class="technologies-section">
          <h3>Tecnologías Utilizadas</h3>
          <div class="tech-grid">
            <span 
              v-for="tech in project.technologies" 
              :key="tech" 
              class="tech-tag"
            >
              {{ tech }}
            </span>
          </div>
        </div>
        
        <div class="actions-section">
          <a 
            v-if="project.demoUrl" 
            :href="project.demoUrl" 
            class="action-button primary"
            target="_blank"
          >
            <i class="fas fa-external-link-alt"></i>
            Ver Demo
          </a>
          <a 
            v-if="project.githubUrl" 
            :href="project.githubUrl" 
            class="action-button secondary"
            target="_blank"
          >
            <i class="fab fa-github"></i>
            Ver Código
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Project {
  id: number
  title: string
  description: string
  longDescription: string
  technologies: string[]
  image: string
  demoUrl?: string
  githubUrl?: string
  status: 'completed' | 'in-progress' | 'concept'
  category: string
}

defineProps<{
  project: Project
}>()

const emit = defineEmits<{
  close: []
}>()

const closeModal = () => {
  emit('close')
}

const getStatusText = (status: string) => {
  const statusMap = {
    'completed': 'Completado',
    'in-progress': 'En Desarrollo',
    'concept': 'Concepto'
  }
  return statusMap[status as keyof typeof statusMap] || status
}
</script>

<style lang="scss" scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  padding: 20px;
}

.modal-content {
  background: white;
  border-radius: 20px;
  max-width: 800px;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
  animation: modalSlideIn 0.3s ease;
}

@keyframes modalSlideIn {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.modal-close {
  position: absolute;
  top: 20px;
  right: 20px;
  background: rgba(255, 255, 255, 0.9);
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 1001;
  transition: all 0.3s ease;
  
  &:hover {
    background: #ff4757;
    color: white;
    transform: scale(1.1);
  }
}

.modal-header {
  position: relative;
  height: 300px;
  overflow: hidden;
  border-radius: 20px 20px 0 0;
}

.modal-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.modal-info {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(transparent, rgba(0,0,0,0.7));
  padding: 40px 30px 30px;
  color: white;
  
  h2 {
    font-size: 2rem;
    font-weight: 700;
    margin: 10px 0 0;
  }
}

.project-meta {
  display: flex;
  gap: 10px;
  margin-bottom: 10px;
}

.project-category {
  background: rgba(255, 255, 255, 0.2);
  color: white;
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 600;
  backdrop-filter: blur(10px);
}

.project-status {
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 600;
  backdrop-filter: blur(10px);
  
  &.completed {
    background: rgba(72, 187, 120, 0.8);
    color: white;
  }
  
  &.in-progress {
    background: rgba(237, 137, 54, 0.8);
    color: white;
  }
  
  &.concept {
    background: rgba(113, 128, 150, 0.8);
    color: white;
  }
}

.modal-body {
  padding: 40px;
}

.description-section,
.technologies-section {
  margin-bottom: 40px;
  
  h3 {
    color: #2d3748;
    font-size: 1.3rem;
    font-weight: 700;
    margin-bottom: 20px;
    padding-bottom: 10px;
    border-bottom: 2px solid #e2e8f0;
  }
  
  p {
    color: #4a5568;
    line-height: 1.7;
    font-size: 1.1rem;
  }
}

.tech-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 12px;
}

.tech-tag {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  padding: 12px 16px;
  border-radius: 12px;
  font-size: 0.9rem;
  font-weight: 600;
  text-align: center;
  transition: transform 0.3s ease;
  
  &:hover {
    transform: translateY(-2px);
  }
}

.actions-section {
  display: flex;
  gap: 20px;
  justify-content: center;
  
  @media (max-width: 768px) {
    flex-direction: column;
  }
}

.action-button {
  padding: 15px 30px;
  border-radius: 12px;
  font-weight: 600;
  text-decoration: none;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  transition: all 0.3s ease;
  min-width: 150px;
  
  &.primary {
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
    
    &:hover {
      transform: translateY(-3px);
      box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
    }
  }
  
  &.secondary {
    background: transparent;
    color: #667eea;
    border: 2px solid #667eea;
    
    &:hover {
      background: #667eea;
      color: white;
      transform: translateY(-3px);
    }
  }
}
</style>