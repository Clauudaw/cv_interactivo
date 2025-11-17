<template>
  <!-- Botón hamburguesa fijo arriba solo en móvil -->
  <nav class="mobile-toggle " >
    <i @click="toggleMobileMenu" type="button" class="fas fa-bars"></i>
    <span class="mobile-menu-label"></span>
  </nav>

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
  </nav>
  <!-- Overlay móvil -->
    <div v-if="isMobileOpen" class="mobile-overlay" @click="closeMobileMenu"></div>
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
    height: 70px;
    width: 100vw;
    padding: 0 1rem;
    background: linear-gradient(90deg, var(--primary-color, #26357b) 0%, var(--secondary-color, #5158b8) 100%);
    color: white;
    font-size: 2rem;
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
  }
}

/* ------------------------------
   NAV LATERAL
------------------------------ */
.navigation {
  position: fixed;
  top: 0;
  left: 0;
  width: 280px;
  height: 100vh;
  background: linear-gradient(180deg, var(--primary-color, #26357b) 0%, var(--secondary-color, #5158b8) 100%);
  color: white;
  display: flex;
  flex-direction: column;
  z-index: 200;
  transition: transform 0.3s ease;
  overflow-y: auto;
}

/* Móvil: menú oculto y se desliza */
@media (max-width: 768px) {
  .navigation {
    width: 100vw;
    height: calc(100vh - 70px);
    top: 70px; /* justo debajo del botón */
    transform: translateX(-100%);
    z-index: 200;
    overflow-y: auto;
  }

  .navigation.mobile-open {
    transform: translateX(0);
    z-index: 201;
  }
}

/* ------------------------------
   OVERLAY MÓVIL
------------------------------ */
.mobile-overlay {
  display: none;

  @media (max-width: 768px) {
    position: fixed;
    top: 70px;
    left: 0;
    width: 100vw;
    height: calc(100vh - 70px);
    background: rgba(0, 0, 0, 0.3);
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.3s ease;
    z-index: 199;
  }
}

.navigation.mobile-open + .mobile-overlay {
  opacity: 1;
  pointer-events: all;
}

/* ------------------------------
   ESTILOS DEL CONTENIDO DEL NAV
------------------------------ */
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
    padding: 2rem 1rem;
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
}

</style>
