<template>
  <div id="app">
    <!-- Navigation -->
    <Navigation @navigate="handleNavigation" :active-section="activeSection" />
    
    <!-- Main Content -->
    <main class="main-content">
      <transition name="fade" mode="out-in">
        <component :is="currentComponent" />
      </transition>
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import Navigation from './components/Navigation.vue'
import CVSection from './components/CV/CVSection.vue'
import ProjectsSection from './components/Projects/ProjectsSection.vue'

// Mapa de secciones -> componente correspondiente
const componentsMap = {
  cv: CVSection,
  projects: ProjectsSection
}

// Estado inicial
const activeSection = ref<'cv' | 'projects'>('cv')
const currentComponent = ref(componentsMap.cv)

// Cambia la sección activa y el componente mostrado
const handleNavigation = (section: 'cv' | 'projects') => {
  activeSection.value = section
  currentComponent.value = componentsMap[section]
}

onMounted(() => {
  // Animación inicial
  document.body.classList.add('loaded')
})
</script>

<style lang="scss">

#app {
  display:flex;
  min-height: 100vh;
}

/* Ajusta el ancho del nav */
.navigation {
  width: 280px;
  flex-shrink: 0; /* evita que el nav se encoja */
  border-right: 1px solid #ddd;
}

/* El main ocupa el resto del espacio */
.main-content {
  flex: 1;
  min-height: 100vh;
  background-color: #f9f9f9;
  padding: 2rem;
  margin-left: 0; /* ✅ ya no hace falta margin-left */
}

/* Vista móvil */
@media (max-width: 768px) {
  #app {
    flex-direction: column; /* ✅ apila nav y main en móvil */
  }

  .navigation {
    width: 100%;
    border-right: none;
  }

  .main-content {
    padding-top: 70px;
  }
}
</style>
