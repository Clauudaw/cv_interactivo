<template>
  <section class="skills-section card">
    <h2 class="section-title">
      <i class="fas fa-code"></i>
      Competencias Técnicas
    </h2>
    
    <div class="skills-categories">
      <div class="skill-category">
        <h3>Lenguajes de Programación</h3>
        <div class="skills-grid">
          <div v-for="skill in programmingLanguages" :key="skill.name" class="skill-item">
            <div class="skill-header">
              <div class="skill-icon" :style="{ backgroundColor: skill.color }">
                <i :class="skill.icon"></i>
              </div>
              <div class="skill-info">
                <h4>{{ skill.name }}</h4>
                <p>{{ skill.description }}</p>
              </div>
            </div>
            <div class="skill-level">
              <div class="skill-bar">
                <div 
                  class="skill-progress" 
                  :style="{ width: skill.level + '%', backgroundColor: skill.color }"
                ></div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="skill-category">
        <h3>Frameworks y Librerías</h3>
        <div class="skills-grid">
          <div v-for="skill in frameworks" :key="skill.name" class="skill-item">
            <div class="skill-header">
              <div class="skill-icon" :style="{ backgroundColor: skill.color }">
                <i :class="skill.icon"></i>
              </div>
              <div class="skill-info">
                <h4>{{ skill.name }}</h4>
                <p>{{ skill.description }}</p>
              </div>
            </div>
            <div class="skill-level">
              <div class="skill-bar">
                <div 
                  class="skill-progress" 
                  :style="{ width: skill.level + '%', backgroundColor: skill.color }"
                ></div>
              </div>
            </div>
          </div>
        </div>
      </div>

     <div class="skill-category">
  <h3>Herramientas y Tecnologías</h3>
  <div class="tools-grid">
    <div v-for="tool in tools" :key="tool.name" class="tool-item">
      <div class="tool-icon" :style="{ backgroundColor: tool.color }">
        <span v-if="tool.svg" v-html="tool.svg"></span>
        <i v-else :class="tool.icon"></i>
      </div>
      <span>{{ tool.name }}</span>
    </div>
  </div>
</div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const programmingLanguages = ref([
  {
    name: 'HTML',
    description: 'Diseño de páginas web con formularios, tablas y contenido multimedia',
    icon: 'fab fa-html5',
    color: '#E34F26',
    level: 90
  },
  {
    name: 'CSS',
    description: 'Creación de diseños responsivos y adaptativos usando media queries y flexbox',
    icon: 'fab fa-css3-alt',
    color: '#1572B6',
    level: 85
  },
  {
    name: 'JavaScript',
    description: 'Desarrollo de aplicaciones interactivas, manipulación del DOM y uso de AJAX',
    icon: 'fab fa-js-square',
    color: '#F7DF1E',
    level: 80
  },
  {
    name: 'PHP',
    description: 'Desarrollo de aplicaciones del lado del servidor y gestión de bases de datos',
    icon: 'fab fa-php',
    color: '#777BB4',
    level: 75
  },
  {
    name: 'Java',
    description: 'Uso de patrones de diseño como MVC',
    icon: 'fab fa-java',
    color: '#007396',
    level: 70
  },
  {
    name: 'MySQL',
    description: 'Manejo de consultas avanzadas, optimización de bases de datos y operaciones CRUD',
    icon: 'fas fa-database',
    color: '#4479A1',
    level: 78
  }
])

const frameworks = ref([
  {
    name: 'Vue.js',
    description: 'Desarrollo de interfaces dinámicas, reutilización de componentes y gestión del estado con Pinia',
    icon: 'fab fa-vuejs',
    color: '#4FC08D',
    level: 82
  },
  {
    name: 'Nuxt.js',
    description: 'Creación de aplicaciones web optimizadas con SSR y generación estática',
    icon: 'fas fa-layer-group',
    color: '#00DC82',
    level: 75
  },
  {
    name: 'Bootstrap',
    description: 'Desarrollo de interfaces responsive con componentes predefinidos',
    icon: 'fab fa-bootstrap',
    color: '#7952B3',
    level: 80
  }
])

const tools = ref([
  { name: 'Git', icon: 'fab fa-git-alt', color: '#F05032' },
  { name: 'Docker', icon: 'fab fa-docker', color: '#2496ED' },
  { 
    name: 'VS Code', 
   svg: `<svg width="24" height="35" viewBox="-0.55 -35 235.1 235.1" xmlns="http://www.w3.org/2000/svg"><style>.st0{fill:#f5f5f5}</style><path class="st0" d="M83.3 143.9l-58 45.2L0 176.5V58.7L25.2 46l57.6 45.3L174 0l60 23.9v186.9l-59.7 24.3-91-91.2zm88.9 15.9V75.3l-54.6 42.3 54.6 42.2zM27.3 144.6L56 118.5 27.3 89.9v54.7z"/></svg>`,
    color: '#0179cb' 
  },
  { name: 'Figma', icon: 'fab fa-figma', color: '#F24E1E' },
  { name: 'GitHub', icon: 'fab fa-github', color: '#181717' }
])

</script>

<style lang="scss" scoped>
.skills-categories {
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.skill-category {
  h3 {
    color: #2d3748;
    font-size: 1.3rem;
    font-weight: 700;
    margin-bottom: 20px;
    padding-bottom: 10px;
    border-bottom: 2px solid #e2e8f0;
  }
}

.skills-grid {
  display: grid;
  gap: 20px;
  
  @media (min-width: 768px) {
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  }
}

.skill-item {
  background: white;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.08);
  border: 1px solid #e2e8f0;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  
  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(0,0,0,0.15);
  }
}

.skill-header {
  display: flex;
  align-items: flex-start;
  gap: 15px;
  margin-bottom: 15px;
}

.skill-icon {
  width: 50px;
  height: 50px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 1.5rem;
  flex-shrink: 0;
}

.skill-info {
  flex: 1;
  
  h4 {
    color: #2d3748;
    font-size: 1.1rem;
    font-weight: 700;
    margin-bottom: 5px;
  }
  
  p {
    color: #718096;
    font-size: 0.9rem;
    line-height: 1.5;
  }
}

.skill-level {
  margin-top: 15px;
}

.skill-bar {
  width: 100%;
  height: 8px;
  background: #e2e8f0;
  border-radius: 4px;
  overflow: hidden;
}

.skill-progress {
  height: 100%;
  border-radius: 4px;
  transition: width 1s ease-in-out;
  position: relative;
  
  &::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
    animation: shimmer 2s infinite;
  }
}

@keyframes shimmer {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

.tools-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 15px;
}

.tool-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 15px 20px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.08);
  border: 1px solid #e2e8f0;
  transition: transform 0.3s ease;
  
  &:hover {
    transform: translateY(-2px);
  }
  
  .tool-icon {
    width: 40px;
    height: 40px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 1.2rem;
  }
  
  span {
    color: #2d3748;
    font-weight: 600;
  }
}
</style>