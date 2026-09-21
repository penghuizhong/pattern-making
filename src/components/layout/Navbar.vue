<script setup lang="ts">
import { ref } from 'vue'
import { Search, Menu, X } from 'lucide-vue-next'

const mobileMenuOpen = ref(false)

function scrollToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

const navLinks = [
  { href: '#hero', label: '首页', active: true },
  { href: '#knowledge', label: '知识库', active: false },
  { href: '#cad-library', label: 'CAD图稿库', active: false },
  { href: '#calculator', label: '公式计算器', active: false },
  { href: '#ai-assistant', label: 'AI助手', active: false, pro: true },
  { href: '#tutorials', label: '制版教程', active: false },
  { href: '#fashion-design', label: '服装设计', active: false },
]
</script>

<template>
  <header class="sticky top-0 z-50 bg-dark-bg/85 backdrop-blur-xl border-b border-dark-border/80">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
      <!-- Logo -->
      <div class="flex items-center space-x-3 cursor-pointer group" @click="scrollToTop">
        <div class="relative flex items-center justify-center w-10 h-10 border-2 border-white rounded-lg group-hover:border-brand-primary transition-colors">
          <div class="w-3 h-3 bg-white rounded-full group-hover:bg-brand-primary transition-colors"></div>
        </div>
        <div>
          <span class="text-xl font-bold tracking-wider text-white block leading-none font-sans">方圆智版</span>
          <span class="text-[10px] text-gray-400 tracking-wider font-mono">AI 服装智能制版</span>
        </div>
      </div>

      <!-- Desktop Nav -->
      <nav class="hidden lg:flex items-center space-x-8 text-sm font-medium">
        <a
          v-for="link in navLinks"
          :key="link.href"
          :href="link.href"
          :class="[
            link.active
              ? 'text-brand-primary border-b-2 border-brand-primary pb-1 transition-all'
              : 'text-gray-300 hover:text-white transition-colors'
          ]"
          class="flex items-center space-x-1.5"
        >
          <span>{{ link.label }}</span>
          <span
            v-if="link.pro"
            class="bg-gradient-to-r from-indigo-500 to-purple-600 text-white text-[10px] px-1.5 py-0.5 rounded-full font-bold shadow-sm shadow-purple-500/50 group-hover:scale-105 transition-transform"
          >PRO</span>
        </a>
      </nav>

      <!-- Right Tools -->
      <div class="flex items-center space-x-5">
        <button class="text-gray-300 hover:text-white p-2 rounded-lg hover:bg-dark-hover transition">
          <Search class="w-5 h-5" />
        </button>
        <div class="w-9 h-9 rounded-full bg-gradient-to-tr from-amber-500 via-yellow-400 to-amber-200 flex items-center justify-center font-bold text-black text-sm shadow-lg shadow-amber-500/20 cursor-pointer hover:scale-105 transition">
          F
        </div>
        <!-- Mobile Menu Toggle -->
        <button class="lg:hidden text-gray-300 hover:text-white p-2" @click="mobileMenuOpen = !mobileMenuOpen">
          <X v-if="mobileMenuOpen" class="w-5 h-5" />
          <Menu v-else class="w-5 h-5" />
        </button>
      </div>
    </div>

    <!-- Mobile Menu -->
    <Transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 -translate-y-2"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-2"
    >
      <div v-if="mobileMenuOpen" class="lg:hidden bg-dark-card border-b border-dark-border px-4 pb-4 space-y-2">
        <a
          v-for="link in navLinks"
          :key="link.href"
          :href="link.href"
          class="block py-2 text-sm text-gray-300 hover:text-white transition-colors"
          @click="mobileMenuOpen = false"
        >
          {{ link.label }}
          <span
            v-if="link.pro"
            class="ml-2 bg-gradient-to-r from-indigo-500 to-purple-600 text-white text-[10px] px-1.5 py-0.5 rounded-full font-bold"
          >PRO</span>
        </a>
      </div>
    </Transition>
  </header>
</template>
