<template>
  <div class="projects-section">
    <div class="projects-header">
      <h1>Mis Proyectos</h1>
      <p>Una selección de los trabajos que demuestran mis habilidades y experiencia</p>
    </div>
    
    <div class="projects-container">
      <div class="projects-grid">
        <ProjectCard 
          v-for="project in projects" 
          :key="project.id"
          :project="project"
          @view-details="viewProjectDetails"
        />
      </div>
    </div>

    <!-- Modal para detalles del proyecto -->
    <ProjectModal 
      v-if="selectedProject"
      :project="selectedProject"
      @close="selectedProject = null"
    />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import ProjectCard from './ProjectCard.vue'
import ProjectModal from './ProjectModal.vue'

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

const selectedProject = ref<Project | null>(null)

const projects = ref<Project[]>([
 {
  id: 1,
  title: "FindTheBeat",
  description: "Plataforma para alquilar espacios de música con gestión de reservas y roles de usuario.",
  longDescription: `Aplicación web para el alquiler de espacios musicales. Permite a usuarios normales reservar espacios, 
    mientras que administradores gestionan espacios, reservas y usuarios. Cuenta con funcionalidades CRUD completas, 
    autenticación, y un diseño moderno e intuitivo.`,
  technologies: ["Html5","JavaScript","Bootstrap", "Sass", "MySQL", "Php"],
  image: "/sala5.png",
  demoUrl: "#",
  githubUrl: "https://github.com/Clauudaw/TFC_FindTheBeat",
  status: "completed",
  category: "Web Application"
},
  {
    id: 2,
    title: "Dashboard Analytics",
    description: "Panel de control interactivo con gráficos en tiempo real y métricas de rendimiento.",
    longDescription: "Dashboard completo para análisis de datos con múltiples visualizaciones interactivas. Desarrollado con Vue.js y Chart.js, permite monitorear métricas en tiempo real, exportar reportes y configurar alertas personalizadas. Incluye sistema de roles y permisos para diferentes niveles de acceso.",
    technologies: ["Vue.js", "Chart.js", "Socket.io", "Node.js", "MongoDB"],
    image: "https://images.pexels.com/photos/590020/pexels-photo-590020.jpeg?auto=compress&cs=tinysrgb&w=800",
    demoUrl: "#",
    githubUrl: "#",
    status: "completed",
    category: "Data Visualization"
  },
  {
    id: 3,
    title: "Task Management App",
    description: "Aplicación de gestión de tareas colaborativa con funciones de equipo y seguimiento de proyectos.",
    longDescription: "Herramienta de productividad diseñada para equipos de trabajo. Permite crear proyectos, asignar tareas, establecer deadlines y monitorear el progreso. Incluye sistema de notificaciones, comentarios colaborativos, tableros Kanban y reportes de productividad. Desarrollada con arquitectura modular y responsive design.",
    technologies: ["Vue.js", "Firebase", "Vuetify", "PWA", "Jest"],
    image: "https://images.pexels.com/photos/3184360/pexels-photo-3184360.jpeg?auto=compress&cs=tinysrgb&w=800",
    demoUrl: "#",
    githubUrl: "#",
    status: "in-progress",
    category: "Productivity"
  }
])

const viewProjectDetails = (project: Project) => {
  selectedProject.value = project
}
</script>

<style lang="scss" scoped>
.projects-section {
  min-height: 100vh;
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
  padding: 40px 0;
}

.projects-header {
  text-align: center;
  max-width: 800px;
  margin: 0 auto 60px;
  padding: 0 20px;
  
  h1 {
    font-size: 3rem;
    font-weight: 700;
    color: #2d3748;
    margin-bottom: 20px;
    background: linear-gradient(135deg, #667eea, #764ba2);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    
    @media (max-width: 768px) {
      font-size: 2.5rem;
    }
  }
  
  p {
    font-size: 1.2rem;
    color: #718096;
    line-height: 1.6;
  }
}

.projects-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 40px;
  
  @media (max-width: 768px) {
    grid-template-columns: 1fr;
    gap: 30px;
  }
}
</style>