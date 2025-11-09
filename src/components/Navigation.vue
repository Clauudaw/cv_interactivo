<template>
  <!-- Botón hamburguesa fijo arriba solo en móvil -->
  <button class="mobile-toggle" @click="toggleMobileMenu">
    <i class="fas fa-bars"></i>
    <span class="mobile-menu-label"></span>
  </button>

  <nav :class="['navigation', { 'mobile-open': isMobileOpen }]">
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
        :class="['nav-item', { active: props.activeSection === 'cv' }]"
        @click="$emit('navigate', 'cv')"
      >
        <i class="fas fa-user-circle"></i>
        <span>Curriculum Vitae</span>
      </button>
      <button 
        :class="['nav-item', { active: props.activeSection === 'projects' }]"
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

    <!-- Overlay móvil -->
    <div v-if="isMobileOpen" class="mobile-overlay" @click="closeMobileMenu"></div>
  </nav>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, ref, watch } from 'vue'

const props = defineProps<{
  activeSection: 'cv' | 'projects'  
}>()

defineEmits<{
  navigate: [section: 'cv' | 'projects'] 
}>()

const isMobileOpen = ref(false)
const toggleMobileMenu = () => { isMobileOpen.value = !isMobileOpen.value }
const closeMobileMenu = () => { isMobileOpen.value = false }

// Cerrar menú móvil al navegar
watch(
  () => props.activeSection,
  () => { closeMobileMenu() }
)
</script>

<style lang="scss">
/* Botón hamburguesa fijo solo en móvil */
.mobile-toggle {
  display: none;
  @media (max-width: 768px) {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    position: fixed;
    top: 0;
    left: 0;
    height: 56px;
    width: 100vw;
    padding-left: 1rem;
    background: linear-gradient(90deg, var(--primary-color, #26357b) 0%, var(--secondary-color, #5158b8) 100%);
    color: white;
    border-radius: 0;
    font-size: 2rem;
    border: none;
    box-sizing: border-box;
    border-bottom: 1px solid rgba(255, 255, 255, 0.63);
    z-index: 300;
    cursor: pointer;
  }
}
.mobile-menu-label {
  display: none;
  margin-left: 0.5rem;
  font-size: 1rem;
  font-weight: 700;
  @media (max-width: 768px) {
    display: inline;
    vertical-align: middle;
  }
}

/* NAV LATERAL */
.navigation {
  position: fixed;
  top: 0;
  left: 0;
  width: 280px;
  height: 100%;
  background: linear-gradient(180deg, var(--primary-color, #26357b) 0%, var(--secondary-color, #5158b8) 100%);
  color: white;
  display: flex;
  flex-direction: column;
  z-index: 100;
  transition: transform 0.3s ease;

  @media (max-width: 768px) {
    width: 80vw;
    max-width: 280px;
    height: 100vh;
    transform: translateX(-100%);
    padding-top: 56px; /* deja sitio al botón arriba */
    z-index: 200;
    &.mobile-open {
      transform: translateX(0);
      z-index: 201;
    }
  }
}

.mobile-overlay {
  display: none;
  z-index: 150;
  @media (max-width: 768px) {
    display: block;
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.1);
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.3s ease;
    z-index: 199;
  }
  .mobile-open & {
    opacity: 1;
    pointer-events: all;
  }
}

.nav-header {
  padding: 2rem;
  text-align: center;
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
  @media (max-width: 768px) {
    display: none;
  }
}
.nav-footer {
  padding: 2rem;
  border-top: 1px solid rgba(255, 255, 255, 0.2);
  @media (max-width: 768px) {
    display: none;
  }
}
.nav-menu {
  flex: 1;
  padding: 1.5rem 0;

  @media (max-width: 768px) {
    padding: 5rem 1rem 2rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
}
.nav-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem 2rem;
  background: none;
  border: none;
  color: white;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  width: 100%;
  &:hover,
  &.active {
    background: rgba(255, 255, 255, 0.2);
    padding-left: 2.5rem;
  }
  i {
    font-size: 1.2rem;
  }
}
.profile-image {
  margin-bottom: 1.5rem;
  .image-placeholder {
    width: 100px;
    height: 100px;
    background: rgba(255, 255, 255, 0.2);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto;
    font-size: 2.5rem;
    backdrop-filter: blur(10px);
  }
}
.nav-title {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}
.nav-subtitle {
  opacity: 0.9;
  font-size: 0.9rem;
  margin: 0;
}
</style>
