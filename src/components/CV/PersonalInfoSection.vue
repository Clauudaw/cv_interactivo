<template>
  <section class="personal-info card">
    <h2 class="section-title">
      <i class="fas fa-info-circle"></i>
      Información
    </h2>
    <div class="info-content">
      <div class="info-item">
        <i class="fas fa-code"></i>
        <span>Formación constante en nuevas tecnologías</span>
      </div>
      <div class="info-item">
        <i class="fas fa-clock"></i>
        <span>Incorporación inmediata</span>
      </div>
      <div class="info-item">
        <i class="fas fa-calendar"></i>
        <span>Flexible en horarios y disponibilidad</span>
      </div>
    </div>
    
    <div class="contact-section">
      <h3>Contacto</h3>
      <div class="contact-grid">
        <a href="tel:622131197" class="contact-item">
          <i class="fas fa-phone"></i>
          <span>622 13 11 97</span>
        </a>
        <a href="mailto:claudiardaw@gmail.com" class="contact-item">
          <i class="fas fa-envelope"></i>
          <span>claudiardaw@gmail.com</span>
        </a>
        <div class="contact-item">
          <i class="fas fa-map-marker-alt"></i>
          <span>San Lorenzo de El Escorial, CP 28200</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.info-content {
  margin-bottom: 30px;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px 0;
  border-bottom: 1px solid #e2e8f0;
  color: #4a5568;
  
  &:last-child {
    border-bottom: none;
  }
  
  i {
    color: #667eea;
    font-size: 1.1rem;
    width: 20px;
  }
  
  span {
    font-weight: 500;
  }
}

.contact-section {
  h3 {
    color: #2d3748;
    font-size: 1.2rem;
    font-weight: 700;
    margin-bottom: 15px;
    padding-bottom: 8px;
    border-bottom: 2px solid #667eea;
  }
}

.contact-grid {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px;
  background: #f7fafc;
  border-radius: 8px;
  color: #4a5568;
  text-decoration: none;
  transition: all 0.3s ease;
  
  &:hover {
    background: #667eea;
    color: white;
    transform: translateX(5px);
  }
  
  i {
    color: #667eea;
    font-size: 1.1rem;
    width: 20px;
    transition: color 0.3s ease;
  }
  
  &:hover i {
    color: white;
  }
  
  span {
    font-weight: 500;
    font-size: 0.9rem;
  }
}
</style>