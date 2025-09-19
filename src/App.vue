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
.main-content {
  margin-left: 280px;
  min-height: 100vh;
  
  @media (max-width: 768px) {
    margin-left: 0;
    padding-top: 70px;
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

body.loaded {
  opacity: 1;
  transform: translateY(0);
}
</style>
