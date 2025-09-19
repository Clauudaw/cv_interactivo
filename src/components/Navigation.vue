<template>
  <nav class="navigation">
    <div class="nav-header">
      <div class="profile-image">
        <div class="image-placeholder">
          <i class="fas fa-user"></i>
        </div>
      </div>
      <h2 class="nav-title">Claudia Rey Benito</h2>
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
  document.querySelector('.nav-menu')?.classList.toggle('mobile-open')
}
</script>

<style lang="scss">
/* Menú de navegación base */
.navigation {
  position: relative;
  padding: 1rem;
  background-color: #242424;
  color: white;
}

.nav-header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.nav-title {
  font-size: 1.8rem;
  margin-top: 0.5rem;
}

.nav-subtitle {
  font-size: 1rem;
  margin-top: 0.2rem;
}

.nav-menu {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 2rem;
}

/* Mobile menu toggle button */
.mobile-toggle {
  display: none;
  background: none;
  border: none;
  color: white;
  font-size: 30px;
  cursor: pointer;
  margin-top: 2rem;
}

/* Estilos para pantallas pequeñas */
@media (max-width: 768px) {
  .nav-menu {
    display: none; /* Inicialmente ocultamos el menú en móviles */
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    background-color: #333;
    color: white;
    padding: 1rem;
    flex-direction: column;
    text-align: center;
    z-index: 9999;
  }

  /* Mostrar el menú cuando la clase 'mobile-open' esté activa */
  .nav-menu.mobile-open {
    display: flex;
  }

  /* Mostrar el icono de hamburguesa en pantallas pequeñas */
  .mobile-toggle {
    display: block;
  }
}

/* Estilo de los botones de la navegación */
.nav-item {
  background-color: #1a1a1a;
  border-radius: 8px;
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 500;
  font-family: inherit;
  color: white;
  cursor: pointer;
  transition: background-color 0.25s ease;
}

.nav-item.active {
  background-color: #646cff;
}

.nav-item:hover {
  background-color: #535bf2;
}
</style>
