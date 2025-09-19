<template>
  <section class="languages card">
    <h2 class="section-title">
      <i class="fas fa-globe"></i>
      Idiomas
    </h2>
    <div class="languages-content">
      <div class="language-item">
        <div class="language-header">
          <h3>Español</h3>
          <span class="level-badge native">Nativo</span>
        </div>
        <div class="language-level">
          <div class="level-bar">
            <div class="level-progress native" style="width: 100%"></div>
          </div>
        </div>
      </div>
      
      <div class="language-item">
        <div class="language-header">
          <h3>Inglés</h3>
          <span class="level-badge intermediate">Nivel B2</span>
        </div>
        <div class="language-level">
          <div class="level-bar">
            <div class="level-progress intermediate" style="width: 75%"></div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.languages-content {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.language-item {
  padding: 20px;
  background: #f7fafc;
  border-radius: 12px;
  border-left: 4px solid #667eea;
}

.language-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
  
  h3 {
    color: #2d3748;
    font-size: 1.1rem;
    font-weight: 700;
    margin: 0;
  }
}

.level-badge {
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 600;
  
  &.native {
    background: linear-gradient(135deg, #48bb78, #38a169);
    color: white;
  }
  
  &.intermediate {
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
  }
}

.language-level {
  margin-top: 10px;
}

.level-bar {
  width: 100%;
  height: 8px;
  background: #e2e8f0;
  border-radius: 4px;
  overflow: hidden;
}

.level-progress {
  height: 100%;
  border-radius: 4px;
  transition: width 1s ease-in-out;
  
  &.native {
    background: linear-gradient(90deg, #48bb78, #38a169);
  }
  
  &.intermediate {
    background: linear-gradient(90deg, #667eea, #764ba2);
  }
}
</style>