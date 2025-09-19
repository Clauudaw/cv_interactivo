<template>
  <section class="profile-section card">
    <h2 class="section-title">
      <i class="fas fa-user"></i>
      Perfil Profesional
    </h2>
    <div class="profile-content">
      <p>
        Como desarrolladora web, busco adquirir experiencia práctica y aplicar mis habilidades en un entorno profesional. 
        Durante mis prácticas en Alebat Education, trabajé con Vue.js, Nuxt y Pinia, desarrollando componentes reutilizables 
        y optimizando la gestión del estado.
      </p>
      <p>
        Me motiva contribuir a proyectos innovadores, aprender de profesionales experimentados y crecer en un entorno de 
        mejora continua. Estoy siempre abierta a nuevos desafíos que me permitan ampliar mis conocimientos y perfeccionar 
        mis habilidades técnicas.
      </p>
      <div class="highlights">
        <div class="highlight-item">
          <i class="fas fa-rocket"></i>
          <span>Orientada a resultados</span>
        </div>
        <div class="highlight-item">
          <i class="fas fa-chart-line"></i>
          <span>Enfoque en crecimiento continuo</span>
        </div>
        <div class="highlight-item">
          <i class="fas fa-users"></i>
          <span>Trabajo en equipo</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.profile-content {
  p {
    margin-bottom: 20px;
    line-height: 1.7;
    color: #4a5568;
  }
}

.highlights {
  display: flex;
  gap: 30px;
  margin-top: 30px;
  
  @media (max-width: 768px) {
    flex-direction: column;
    gap: 15px;
  }
}

.highlight-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 15px 20px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  border-radius: 12px;
  font-weight: 600;
  transition: transform 0.3s ease;
  
  &:hover {
    transform: translateY(-3px);
  }
  
  i {
    font-size: 1.2rem;
  }
}
</style>