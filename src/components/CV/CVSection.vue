<template>
  <div class="cv-section">
    <HeroSection />
    <div class="cv-content">
      <div class="cv-grid">
        <div class="main-content-area">
          <ProfileSection />
          <ExperienceSection />
          <SkillsSection />
        </div>
        <div class="sidebar-content">
          <PersonalInfoSection />
          <LanguagesSection />
          <SoftSkillsSection />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import HeroSection from './HeroSection.vue'
import ProfileSection from './ProfileSection.vue'
import ExperienceSection from './ExperienceSection.vue'
import SkillsSection from './SkillsSection.vue'
import PersonalInfoSection from './PersonalInfoSection.vue'
import LanguagesSection from './LanguagesSection.vue'
import SoftSkillsSection from './SoftSkillsSection.vue'
</script>

<style lang="scss" scoped>
.cv-section {
  min-height: 100vh;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.cv-content {
  background: #f8f9fa;
  min-height: calc(100vh - 400px);
  padding: 40px 0;
}

.cv-grid {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 40px;
  
  @media (max-width: 768px) {
    grid-template-columns: 1fr;
    gap: 30px;
  }
}

.main-content-area {
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.sidebar-content {
  display: flex;
  flex-direction: column;
  gap: 30px;
}
</style>