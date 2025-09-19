<template>
  <section class="hero-section">
    <div class="hero-content">
      <div class="hero-text">
        <h1 class="hero-title">
          <span class="name">Claudia Rey Benito</span>
          <span class="title">Desarrolladora Web Junior</span>
        </h1>
        <p class="hero-description">
          Apasionada por crear experiencias web modernas e innovadoras con tecnologías de vanguardia.
        </p>
        <div class="hero-buttons">
          <a 
            href="/claudia_rey_cv.pdf" 
            download="ClaudiaReyBenito_CV.pdf" 
            class="btn-primary"
          >
            <i class="fas fa-download"></i>
            Descargar CV
          </a>
         <a
          href="https://wa.me/34622131197"
          target="_blank"
          rel="noopener noreferrer"
          class="btn-secondary"
        >
          <i class="fab fa-whatsapp"></i>
          Contactar
        </a>
        </div>
      </div>
      <div class="hero-visual">
        <div class="floating-elements">
          <div class="tech-icon vue"><i class="fab fa-vuejs"></i></div>
          <div class="tech-icon js"><i class="fab fa-js-square"></i></div>
          <div class="tech-icon php"><i class="fab fa-php"></i></div>
          <div class="tech-icon html"><i class="fab fa-html5"></i></div>
          <div class="tech-icon css"><i class="fab fa-css3-alt"></i></div>
          <div class="tech-icon git"><i class="fab fa-git-alt"></i></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
defineEmits<{
  contact: []
}>()
</script>

<style lang="scss" scoped>
.hero-section {
  height: 400px;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.hero-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  gap: 60px;
  
  @media (max-width: 768px) {
    grid-template-columns: 1fr;
    text-align: center;
    gap: 30px;
  }
}

.hero-title {
  margin: 0 0 20px 0;
  
  .name {
    display: block;
    font-size: 3.5rem;
    font-weight: 700;
    color: white;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
    
    @media (max-width: 768px) {
      font-size: 2.5rem;
    }
  }
  
  .title {
    display: block;
    font-size: 1.5rem;
    font-weight: 400;
    color: #e2e8f0;
    margin-top: 10px;
    
    @media (max-width: 768px) {
      font-size: 1.2rem;
    }
  }
}

.hero-description {
  font-size: 1.1rem;
  color: #e2e8f0;
  line-height: 1.6;
  margin-bottom: 30px;
  max-width: 500px;
}

.hero-buttons {
  display: flex;
  gap: 15px;
  
  @media (max-width: 768px) {
    justify-content: center;
    flex-wrap: wrap;
  }
}

.btn-primary, .btn-secondary {
  padding: 12px 24px;
  border: none;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 8px;
  
  i {
    font-size: 1rem;
  }
}

.btn-primary {
  background: white;
  color: #667eea;
  
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(0,0,0,0.2);
  }
}

.btn-secondary {
  background: transparent;
  color: white;
  border: 2px solid white;
  
  &:hover {
    background: white;
    color: #667eea;
    transform: translateY(-2px);
  }
}

.floating-elements {
  position: relative;
  height: 300px;
  
  .tech-icon {
    position: absolute;
    width: 60px;
    height: 60px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
    color: white;
    animation: float 6s ease-in-out infinite;
    
    &.vue {
      background: #4FC08D;
      top: 10%;
      left: 20%;
      animation-delay: 0s;
    }
    
    &.js {
      background: #F7DF1E;
      color: #000;
      top: 30%;
      right: 10%;
      animation-delay: 1s;
    }
    
    &.php {
      background: #777BB4;
      bottom: 40%;
      left: 10%;
      animation-delay: 2s;
    }
    
    &.html {
      background: #E34F26;
      top: 60%;
      right: 30%;
      animation-delay: 3s;
    }
    
    &.css {
      background: #1572B6;
      bottom: 10%;
      left: 40%;
      animation-delay: 4s;
    }
    
    &.git {
      background: #F05032;
      top: 45%;
      left: 50%;
      animation-delay: 5s;
    }
  }
}

@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-20px) rotate(10deg); }
}
</style>