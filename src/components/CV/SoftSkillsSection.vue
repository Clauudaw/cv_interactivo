<template>
  <section class="soft-skills card">
    <h2 class="section-title">
      <i class="fas fa-heart"></i>
      Habilidades
    </h2>
    <div class="skills-grid">
      <div v-for="skill in softSkills" :key="skill.name" class="skill-item">
        <div class="skill-icon">
          <i :class="skill.icon"></i>
        </div>
        <h3>{{ skill.name }}</h3>
        <p>{{ skill.description }}</p>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const softSkills = ref([
  {
    name: 'Comunicación Asertiva',
    description: 'Capacidad para expresar ideas de forma clara y constructiva',
    icon: 'fas fa-comments'
  },
  {
    name: 'Trabajo en Equipo',
    description: 'Colaboración efectiva y apoyo mutuo en proyectos grupales',
    icon: 'fas fa-users'
  },
  {
    name: 'Resolución de Problemas',
    description: 'Análisis crítico y búsqueda de soluciones creativas',
    icon: 'fas fa-puzzle-piece'
  },
  {
    name: 'Proactividad',
    description: 'Iniciativa personal y anticipación a las necesidades del proyecto',
    icon: 'fas fa-rocket'
  },
  {
    name: 'Adaptabilidad',
    description: 'Capacidad para ajustarse a cambios y nuevas situaciones de manera efectiva',
    icon: 'fas fa-sync-alt'
  },
  {
    name: 'Manejo del Estrés',
    description: 'Capacidad para mantener la calma y eficiencia bajo presión',
    icon: 'fas fa-balance-scale'
  }
])
</script>

<style lang="scss" scoped>
.skills-grid {
  display: grid;
  gap: 20px;
}

.skill-item {
  text-align: center;
  padding: 25px 20px;
  background: linear-gradient(135deg, #f7fafc, #edf2f7);
  border-radius: 12px;
  border: 1px solid #e2e8f0;
  transition: all 0.3s ease;
  
  &:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 30px rgba(102, 126, 234, 0.15);
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
    
    .skill-icon {
      background: white;
      color: #667eea;
      transform: scale(1.1);
    }
  }
}

.skill-icon {
  width: 60px;
  height: 60px;
  margin: 0 auto 15px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  transition: all 0.3s ease;
}

h3 {
  color: #2d3748;
  font-size: 1.1rem;
  font-weight: 700;
  margin-bottom: 10px;
  transition: color 0.3s ease;
}

p {
  color: #718096;
  font-size: 0.9rem;
  line-height: 1.4;
  margin: 0;
  transition: color 0.3s ease;
}

.skill-item:hover {
  h3, p {
    color: white;
  }
}
</style>