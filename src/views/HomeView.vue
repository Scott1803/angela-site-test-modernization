<script setup lang="ts">
import { useReveal } from '../composables/useReveal'
import HeroSection from '../components/HeroSection.vue'
import ServicesPreview from '../components/ServicesPreview.vue'
import SeeleSection from '../components/SeeleSection.vue'
import ClientLogos from '../components/ClientLogos.vue'
import CtaBanner from '../components/CtaBanner.vue'

useReveal()
</script>

<template>
  <main>
    <HeroSection />
    <ServicesPreview />
    <SeeleSection />
    <ClientLogos />
    <CtaBanner />
  </main>
</template>
