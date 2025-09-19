<template>
  <div class="project-card">
    <div class="project-image">
      <img :src="project.image" :alt="project.title" />
      <div class="project-overlay">
        <div class="project-actions">
          <button @click="$emit('view-details', project)" class="btn-details">
            <i class="fas fa-eye"></i>
            Ver Detalles
          </button>
          <a v-if="project.demoUrl" :href="project.demoUrl" class="btn-demo" target="_blank">
            <i class="fas fa-external-link-alt"></i>
            Demo
          </a>
        </div>
      </div>
    </div>
    
    <div class="project-content">
      <div class="project-meta">
        <span class="project-category">{{ project.category }}</span>
        <span :class="['project-status', project.status]">
          {{ getStatusText(project.status) }}
        </span>
      </div>
      
      <h3 class="project-title">{{ project.title }}</h3>
      <p class="project-description">{{ project.description }}</p>
      
      <div class="project-technologies">
        <span 
          v-for="tech in project.technologies.slice(0, 4)" 
          :key="tech" 
          class="tech-tag"
        >
          {{ tech }}
        </span>
        <span v-if="project.technologies.length > 4" class="tech-more">
          +{{ project.technologies.length - 4 }} más
        </span>
      </div>
      
      <div class="project-links">
        <button @click="$emit('view-details', project)" class="link-button primary">
          <i class="fas fa-info-circle"></i>
          Más Info
        </button>
        <a v-if="project.githubUrl" :href="project.githubUrl" class="link-button secondary" target="_blank">
          <i class="fab fa-github"></i>
          Código
        </a>
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

defineEmits<{
  'view-details': [project: Project]
}>()

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
.project-card {
  background: white;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0,0,0,0.1);
  transition: all 0.3s ease;
  
  &:hover {
    transform: translateY(-10px);
    box-shadow: 0 20px 40px rgba(0,0,0,0.15);
  }
}

.project-image {
  position: relative;
  height: 250px;
  overflow: hidden;
  
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
  }
  
  &:hover img {
    transform: scale(1.1);
  }
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(102, 126, 234, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
  
  .project-card:hover & {
    opacity: 1;
  }
}

.project-actions {
  display: flex;
  gap: 15px;
}

.btn-details,
.btn-demo {
  padding: 12px 24px;
  background: white;
  color: #667eea;
  border: none;
  border-radius: 8px;
  font-weight: 600;
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  
  &:hover {
    background: #667eea;
    color: white;
    transform: translateY(-2px);
  }
}

.project-content {
  padding: 30px;
}

.project-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
}

.project-category {
  background: #e2e8f0;
  color: #4a5568;
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 600;
}

.project-status {
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 600;
  
  &.completed {
    background: #c6f6d5;
    color: #22543d;
  }
  
  &.in-progress {
    background: #fef5e7;
    color: #744210;
  }
  
  &.concept {
    background: #e2e8f0;
    color: #4a5568;
  }
}

.project-title {
  color: #2d3748;
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 15px;
}

.project-description {
  color: #718096;
  line-height: 1.6;
  margin-bottom: 20px;
}

.project-technologies {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 25px;
}

.tech-tag {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  padding: 6px 12px;
  border-radius: 15px;
  font-size: 0.8rem;
  font-weight: 500;
}

.tech-more {
  background: #e2e8f0;
  color: #4a5568;
  padding: 6px 12px;
  border-radius: 15px;
  font-size: 0.8rem;
  font-weight: 500;
}

.project-links {
  display: flex;
  gap: 15px;
}

.link-button {
  padding: 12px 20px;
  border: none;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 8px;
  transition: all 0.3s ease;
  
  &.primary {
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
    
    &:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 20px rgba(102, 126, 234, 0.3);
    }
  }
  
  &.secondary {
    background: transparent;
    color: #667eea;
    border: 2px solid #667eea;
    
    &:hover {
      background: #667eea;
      color: white;
      transform: translateY(-2px);
    }
  }
}
</style>