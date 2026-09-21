<script setup lang="ts">
import Navbar from '@/components/layout/Navbar.vue'
import FooterSection from '@/components/layout/FooterSection.vue'
import HeroSection from '@/components/sections/HeroSection.vue'
import CadLibrarySection from '@/components/sections/CadLibrarySection.vue'
import CalculatorSection from '@/components/sections/CalculatorSection.vue'
import AIAssistantSection from '@/components/sections/AIAssistantSection.vue'
import TutorialsSection from '@/components/sections/TutorialsSection.vue'
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <Navbar />

    <main class="flex-1">
      <HeroSection />
      <CadLibrarySection />
      <CalculatorSection />
      <AIAssistantSection />
      <TutorialsSection />
    </main>

    <FooterSection />
  </div>
</template>
