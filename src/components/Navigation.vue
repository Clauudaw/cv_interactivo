<template>
  <nav class="navigation">
    <!-- Botón hamburguesa (visible solo en móvil) -->
    <button class="mobile-toggle" @click="toggleMobileMenu">
      <i class="fas fa-bars"></i>
    </button>

    <div class="nav-header">
      <div class="profile-image">
        <div class="image-placeholder">
          <i class="fas fa-user"></i>
        </div>
      </div>
      <h2 class="nav-title">Claudia Rey Benito</h2>
      <p class="nav-subtitle">Desarrolladora Web</p>
    </div>

    <!-- Menú principal -->
    <div class="nav-menu">
      <button 
        :class="['nav-item', { active: activeSection === 'cv' }]"
        @click="$emit('navigate', 'cv')"
      >
        <i class="fas fa-user-circle"></i>
        <span>Curriculum Vitae</span>
      </button>
      <button 
        :class="['nav-item', { active: activeSection === 'projects' }]"
        @click="$emit('navigate', 'projects')"
      >
        <i class="fas fa-folder-open"></i>
        <span>Proyectos</span>
      </button>
    </div>

    <div class="nav-footer">
      <div class="contact-info">
        <div class="contact-item">
          <i class="fas fa-user-tie"></i>
          <span><b>CV desarrollado por Claudia Rey Benito</b></span>
        </div>
      </div>
    </div>
  </nav>
</template>
<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'

// Definir las propiedades esperadas
defineProps<{
  activeSection: 'cv' | 'projects'  
}>()

// Definir los eventos emitidos
defineEmits<{
  navigate: [section: 'cv' | 'projects'] 
}>()

const toggleMobileMenu = () => {
  document.querySelector('.navigation')?.classList.toggle('mobile-open')
}
</script>

<style scoped>

.navigation {
  position: relative;
  background: #fff;
  padding: 1rem;

  .nav-menu {
    display: flex;
    flex-direction: column;
  }

  .mobile-toggle {
    display: none;
    position: absolute;
    top: 1rem;
    right: 1rem;
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
  }

  /* Estilos móviles */
  @media (max-width: 768px) {
    .nav-menu {
      display: none;
      flex-direction: column;
      gap: 1rem;
    }

    &.mobile-open .nav-menu {
      display: flex;
    }

    .mobile-toggle {
      display: block;
    }
  }
}
</style>
