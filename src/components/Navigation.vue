<template>
  <nav class="navigation">
    <div class="nav-header">
      <div class="profile-image">
        <div class="image-placeholder">
          <i class="fas fa-user"></i>
        </div>
      </div>
      <h2 class="nav-title">Claudia Rey</h2>
      <p class="nav-subtitle">Desarrolladora Web</p>
    </div>

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

    <!-- Mobile menu toggle -->
    <button class="mobile-toggle" @click="toggleMobileMenu">
      <i class="fas fa-bars"></i>
    </button>
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
