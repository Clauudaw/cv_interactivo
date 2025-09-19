<template>
  <section class="experience-section card">
    <h2 class="section-title">
      <i class="fas fa-graduation-cap"></i>
      Formación
    </h2>
    <div class="timeline">
      <div class="timeline-item">
        <div class="timeline-marker"></div>
        <div class="timeline-content">
          <h3>Grado Superior en Desarrollo de Aplicaciones Web (DAW)</h3>
          <p class="timeline-subtitle">IES Juan de Herrera - San Lorenzo de El Escorial</p>
          <p class="timeline-date">2022 - 2024</p>
          <p class="timeline-description">
            Prácticas profesionales en Alebat Education, donde trabajé con Vue.js, Nuxt y Pinia, 
            desarrollando componentes reutilizables y optimizando la gestión del estado.
          </p>
          <div class="skills-practiced">
            <span class="skill-tag">Vue.js</span>
            <span class="skill-tag">Nuxt.js</span>
            <span class="skill-tag">Pinia</span>
            <span class="skill-tag">JavaScript</span>
          </div>
        </div>
      </div>
      
      <div class="timeline-item">
        <div class="timeline-marker"></div>
        <div class="timeline-content">
          <h3>Estudios en Derecho</h3>
          <p class="timeline-subtitle">Universidad Nacional de Educación a Distancia (UNED)</p>
          <p class="timeline-date">2020 - 2022</p>
          <p class="timeline-description">
            Formación en análisis crítico, investigación y resolución de problemas complejos. 
            Desarrollé habilidades de comunicación escrita y pensamiento lógico.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.timeline {
  position: relative;
  padding-left: 30px;
  
  &::before {
    content: '';
    position: absolute;
    left: 15px;
    top: 0;
    bottom: 0;
    width: 2px;
    background: linear-gradient(180deg, #667eea, #764ba2);
  }
}

.timeline-item {
  position: relative;
  margin-bottom: 40px;
  
  &:last-child {
    margin-bottom: 0;
  }
}

.timeline-marker {
  position: absolute;
  left: -37px;
  top: 8px;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: #667eea;
  border: 3px solid white;
  box-shadow: 0 0 0 3px #667eea;
}

.timeline-content {
  background: white;
  padding: 25px;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.08);
  border-left: 4px solid #667eea;
  
  h3 {
    color: #2d3748;
    font-size: 1.3rem;
    font-weight: 700;
    margin-bottom: 8px;
  }
  
  .timeline-subtitle {
    color: #667eea;
    font-weight: 600;
    margin-bottom: 5px;
  }
  
  .timeline-date {
    color: #a0aec0;
    font-size: 0.9rem;
    font-weight: 500;
    margin-bottom: 15px;
  }
  
  .timeline-description {
    color: #4a5568;
    line-height: 1.6;
    margin-bottom: 15px;
  }
}

.skills-practiced {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.skill-tag {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 500;
}
</style>