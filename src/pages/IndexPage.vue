<template>
  <q-page class="landing-page">
    <AppNavbar />
    <HeroSection />
    <AboutSection />
    <WhatWeDoSection />
    <HowItWorksSection />
    <BenefitsSection />
    <DifferentialsSection />
    <PlansSection />
    <AudienceSection />
    <MissionSection />

    <AppFooter />

    <q-page-sticky position="bottom-right" :offset="[24, 24]" class="whatsapp-fab">
      <q-btn
        fab
        unelevated
        icon="mdi-whatsapp"
        aria-label="Falar com a Movve no WhatsApp"
        href="https://wa.me/5548992229310"
        target="_blank"
        rel="noopener noreferrer"
      />
    </q-page-sticky>
  </q-page>
</template>

<script setup>
import AboutSection from 'components/landing/AboutSection.vue'
import AudienceSection from 'components/landing/AudienceSection.vue'
import AppFooter from 'components/landing/AppFooter.vue'
import AppNavbar from 'components/landing/AppNavbar.vue'
import BenefitsSection from 'components/landing/BenefitsSection.vue'
import DifferentialsSection from 'components/landing/DifferentialsSection.vue'
import HeroSection from 'components/landing/HeroSection.vue'
import HowItWorksSection from 'components/landing/HowItWorksSection.vue'
import MissionSection from 'components/landing/MissionSection.vue'
import PlansSection from 'components/landing/PlansSection.vue'
import WhatWeDoSection from 'components/landing/WhatWeDoSection.vue'
</script>

<style lang="scss" scoped>
.whatsapp-fab {
  z-index: 1200;
}

.whatsapp-fab :deep(.q-btn) {
  background: #25d366;
  color: #ffffff;
  box-shadow: 0 16px 38px rgba(37, 211, 102, 0.34);
  transition:
    transform 180ms ease,
    box-shadow 180ms ease;
}

.whatsapp-fab :deep(.q-btn:hover) {
  transform: translateY(-2px);
  box-shadow: 0 20px 48px rgba(37, 211, 102, 0.4);
}
</style>
