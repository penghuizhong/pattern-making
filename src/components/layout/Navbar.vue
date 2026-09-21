<script setup lang="ts">
import { ref, onMounted } from 'vue'
import {
  Search,
  Menu,
  X,
  ExternalLink,
  Sun,
  Moon,
  ChevronDown,
  LayoutDashboard,
  Settings,
  LogOut,
  Sparkles,
} from 'lucide-vue-next'

const mobileMenuOpen = ref(false)
const userMenuOpen = ref(false)
const isLightTheme = ref(false)

// 服装设计网站地址
const fashionDesignUrl = 'https://sheji.fangyuan-ai.com'

// 初始化主题（从 localStorage 读取，与 index.html 中的防闪烁脚本同步）
onMounted(() => {
  isLightTheme.value = document.documentElement.classList.contains('light-theme')
})

const navLinks = [
  { href: '#hero', label: '首页', active: true },
  { href: '#ai-pattern', label: 'AI制版', active: false, pro: true },
  { href: '#knowledge', label: '知识库', active: false },
  { href: '#cad-library', label: 'CAD图稿库', active: false },
  { href: '#calculator', label: '制版工具', active: false },
  { href: '#tutorials', label: '制版教程', active: false },
]

function scrollToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

function goToFashionDesign() {
  window.open(fashionDesignUrl, '_blank')
}

function toggleUserMenu() {
  userMenuOpen.value = !userMenuOpen.value
}

function toggleTheme() {
  isLightTheme.value = !isLightTheme.value
  if (isLightTheme.value) {
    document.documentElement.classList.add('light-theme')
    localStorage.setItem('theme', 'light')
  } else {
    document.documentElement.classList.remove('light-theme')
    localStorage.setItem('theme', 'dark')
  }
}
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
              : 'text-gray-300 hover:text-white border-b-2 border-transparent pb-1 hover:border-white/30 transition-colors'
          ]"
          class="flex items-center space-x-1.5"
        >
          <span>{{ link.label }}</span>
          <span
            v-if="link.pro"
            class="bg-gradient-to-r from-indigo-500 to-purple-600 text-white text-[10px] px-1.5 py-0.5 rounded-full font-bold shadow-sm shadow-purple-500/50 group-hover:scale-105 transition-transform"
          >PRO</span>
        </a>
        <!-- 服装设计 - 重点突出，跳转联动 -->
        <button
          @click="goToFashionDesign"
          class="ml-2 px-4 py-1.5 text-sm font-bold rounded-full bg-gradient-to-r from-brand-500 to-brand-400 text-black shadow-lg shadow-brand-500/30 hover:shadow-brand-500/50 hover:scale-105 transition-all flex items-center gap-1.5 group"
        >
          <Sparkles class="h-3.5 w-3.5" />
          <span>服装设计</span>
          <ExternalLink class="h-3 w-3 opacity-70 group-hover:translate-x-0.5 transition-transform" />
        </button>
      </nav>

      <!-- Right Tools -->
      <div class="flex items-center space-x-4">
        <button class="text-gray-300 hover:text-white p-2 rounded-lg hover:bg-dark-hover transition">
          <Search class="w-5 h-5" />
        </button>
        <!-- Theme Toggle -->
        <button
          @click="toggleTheme"
          class="text-gray-300 hover:text-brand-primary p-2 rounded-lg hover:bg-dark-hover transition-all group"
          :title="isLightTheme ? '切换到深色模式' : '切换到浅色模式'"
        >
          <Sun v-if="!isLightTheme" class="w-5 h-5 transition-transform group-hover:rotate-45" />
          <Moon v-else class="w-5 h-5 transition-transform group-hover:-rotate-12" />
        </button>
        <!-- User Menu Dropdown -->
        <div class="relative">
          <button
            class="flex items-center gap-2 group"
            @click="toggleUserMenu"
          >
            <div class="w-9 h-9 rounded-full bg-gradient-to-tr from-amber-500 via-yellow-400 to-amber-200 flex items-center justify-center font-bold text-black text-sm shadow-lg shadow-amber-500/20 hover:scale-105 transition">
              <span class="font-bold">钟</span>
            </div>
            <ChevronDown class="h-4 w-4 text-gray-400 hidden sm:block transition-transform group-hover:text-white" :class="userMenuOpen ? 'rotate-180' : ''" />
          </button>
          <!-- Dropdown Panel -->
          <Transition
            enter-active-class="transition duration-150 ease-out"
            enter-from-class="opacity-0 -translate-y-1"
            enter-to-class="opacity-100 translate-y-0"
            leave-active-class="transition duration-100 ease-in"
            leave-from-class="opacity-100 translate-y-0"
            leave-to-class="opacity-0 -translate-y-1"
          >
            <div
              v-if="userMenuOpen"
              class="absolute right-0 top-full mt-2 w-56 glass-card rounded-xl border border-dark-border/80 py-2 shadow-2xl shadow-black/50 z-50"
            >
              <!-- User Info -->
              <div class="px-4 py-3 border-b border-white/5">
                <div class="flex items-center gap-3">
                  <div class="h-10 w-10 rounded-full bg-gradient-to-tr from-amber-500 via-yellow-400 to-amber-200 flex items-center justify-center font-bold text-black text-sm shadow-lg shadow-amber-500/20 flex-shrink-0">
                    <span class="font-bold">钟</span>
                  </div>
                  <div class="min-w-0">
                    <div class="text-sm font-semibold text-white truncate">钟总</div>
                    <div class="text-xs text-gray-400 truncate">zhong@fangyuan-ai.com</div>
                  </div>
                </div>
              </div>
              <!-- Menu Items -->
              <div class="py-1">
                <button
                  class="w-full flex items-center gap-3 px-4 py-2.5 text-sm text-gray-300 hover:bg-dark-hover hover:text-white transition-colors"
                >
                  <LayoutDashboard class="h-4 w-4 text-brand-primary" />
                  <span class="flex-1 text-left">我的工作台</span>
                  <span class="text-[10px] text-brand-primary bg-brand-primary/10 px-1.5 py-0.5 rounded-full font-bold">PRO</span>
                </button>
                <button
                  class="w-full flex items-center gap-3 px-4 py-2.5 text-sm text-gray-300 hover:bg-dark-hover hover:text-white transition-colors"
                >
                  <Settings class="h-4 w-4 text-gray-400" />
                  <span class="flex-1 text-left">账户设置</span>
                </button>
              </div>
              <div class="border-t border-white/5 pt-1">
                <button
                  class="w-full flex items-center gap-3 px-4 py-2.5 text-sm text-red-400 hover:bg-red-500/10 transition-colors"
                >
                  <LogOut class="h-4 w-4" />
                  <span class="flex-1 text-left">退出登录</span>
                </button>
              </div>
            </div>
          </Transition>
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
        <!-- 服装设计 - 移动端 -->
        <button
          @click="goToFashionDesign(); mobileMenuOpen = false"
          class="w-full mt-2 px-4 py-2.5 text-sm font-bold rounded-full bg-gradient-to-r from-brand-500 to-brand-400 text-black flex items-center justify-center gap-2"
        >
          <Sparkles class="h-4 w-4" />
          <span>服装设计</span>
          <ExternalLink class="h-3.5 w-3.5" />
        </button>
      </div>
    </Transition>
  </header>
</template>
