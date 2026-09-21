<script setup lang="ts">
import { ref } from 'vue'
import { Sparkles, Layers, Cpu, RefreshCw } from 'lucide-vue-next'

const isSuit = ref(true)
const patternPath = ref('M 140,60 Q 170,50 200,60 L 200,360 L 90,360 L 80,220 Q 70,160 110,120 Z')

function togglePattern() {
  if (isSuit.value) {
    patternPath.value = 'M 140,60 Q 165,55 200,60 L 200,360 L 100,360 L 90,240 Q 75,170 120,120 Z'
  } else {
    patternPath.value = 'M 140,60 Q 170,50 200,60 L 200,360 L 90,360 L 80,220 Q 70,160 110,120 Z'
  }
  isSuit.value = !isSuit.value
}
</script>

<template>
  <section id="hero" class="relative min-h-[calc(100vh-4rem)] flex items-center overflow-hidden border-b border-dark-border">
    <!-- 1. Fashion Background -->
    <div class="absolute inset-0 hero-bg-fashion scale-105"></div>

    <!-- 2. Gradient Overlays + CAD Grid -->
    <div class="absolute inset-0 bg-gradient-to-r from-dark-bg via-dark-bg/85 to-dark-bg/40"></div>
    <div class="absolute inset-0 bg-gradient-to-t from-dark-bg via-transparent to-dark-bg/60"></div>
    <div class="absolute inset-0 cad-overlay-grid opacity-60"></div>

    <!-- Neon Glow -->
    <div class="absolute top-1/3 left-1/4 w-[500px] h-[500px] bg-brand-primary/15 blur-[140px] rounded-full pointer-events-none glow-effect"></div>
    <div class="absolute bottom-10 right-10 w-[400px] h-[400px] bg-purple-600/15 blur-[120px] rounded-full pointer-events-none"></div>

    <!-- 3. Content -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20 relative z-10 w-full">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">

        <!-- Left: Text + CTA -->
        <div class="lg:col-span-7 space-y-8 text-center lg:text-left">
          <div class="inline-flex items-center space-x-2 bg-dark-card/90 border border-brand-primary/40 px-4 py-1.5 rounded-full text-xs text-brand-primary backdrop-blur-md">
            <span class="inline-block w-2 h-2 rounded-full bg-brand-primary animate-ping"></span>
            <span class="font-mono tracking-wide">AI Engine v3.5 · 工业级打版与自动推码引擎</span>
          </div>

          <h1 class="text-4xl sm:text-6xl xl:text-7xl font-extrabold text-white tracking-tight leading-[1.1]">
            时尚审美 <span class="text-transparent bg-clip-text bg-gradient-to-r from-brand-primary via-amber-300 to-yellow-500">× AI算力</span>
            <span class="block text-3xl sm:text-5xl xl:text-6xl font-normal text-gray-200 mt-2">重新定义服装智能制版</span>
          </h1>

          <p class="text-gray-300 text-base sm:text-lg max-w-2xl mx-auto lg:mx-0 leading-relaxed font-light">
            融汇高级时装结构原理与神经网络算法。从自然语言 Prompt 到毫米级矢量 CAD 样板，将数小时的繁琐手工推码，缩短至秒级生成。
          </p>

          <!-- CTA Buttons -->
          <div class="flex flex-col sm:flex-row items-center justify-center lg:justify-start gap-4 pt-2">
            <a href="#ai-assistant" class="w-full sm:w-auto px-8 py-4 bg-gradient-to-r from-brand-primary to-amber-500 hover:from-amber-400 hover:to-yellow-400 text-black font-bold rounded-xl shadow-xl shadow-brand-primary/25 hover:scale-[1.02] active:scale-[0.98] transition-all flex items-center justify-center space-x-2">
              <Sparkles class="w-5 h-5" />
              <span>立即体验 AI 智能制版</span>
            </a>
            <a href="#cad-library" class="w-full sm:w-auto px-8 py-4 glass-card hover:bg-dark-hover text-white font-semibold rounded-xl border border-gray-600/60 hover:border-brand-primary/60 transition-all flex items-center justify-center space-x-2">
              <Layers class="w-5 h-5 text-brand-primary" />
              <span>浏览 CAD 图稿资源库</span>
            </a>
          </div>

          <!-- Metrics -->
          <div class="grid grid-cols-3 gap-4 pt-8 border-t border-white/10 max-w-xl mx-auto lg:mx-0">
            <div>
              <div class="text-2xl sm:text-3xl font-extrabold text-white font-mono">85%<span class="text-brand-primary text-base">+</span></div>
              <div class="text-xs text-gray-400 mt-1">制版效率提升</div>
            </div>
            <div>
              <div class="text-2xl sm:text-3xl font-extrabold text-white font-mono">0.1<span class="text-xs text-gray-400">mm</span></div>
              <div class="text-xs text-gray-400 mt-1">矢量推码精度</div>
            </div>
            <div>
              <div class="text-2xl sm:text-3xl font-extrabold text-white font-mono">15,000<span class="text-brand-primary text-base">+</span></div>
              <div class="text-xs text-gray-400 mt-1">标准原型版型库</div>
            </div>
          </div>
        </div>

        <!-- Right: CAD HUD Panel -->
        <div class="lg:col-span-5">
          <div class="glass-card-gold p-4 rounded-2xl shadow-2xl relative group overflow-hidden">
            <!-- Scanline -->
            <div class="absolute inset-x-0 h-1 bg-gradient-to-r from-transparent via-brand-primary to-transparent animate-scan opacity-40 pointer-events-none"></div>

            <!-- Panel Header -->
            <div class="flex items-center justify-between pb-3 border-b border-white/10 text-xs font-mono text-gray-300">
              <div class="flex items-center space-x-2">
                <span class="w-2.5 h-2.5 rounded-full bg-red-500"></span>
                <span class="w-2.5 h-2.5 rounded-full bg-yellow-500"></span>
                <span class="w-2.5 h-2.5 rounded-full bg-green-500"></span>
                <span class="ml-2 text-white font-bold">HIGH_COUTURE_SUIT_V2.DXF</span>
              </div>
              <span class="bg-brand-primary/20 text-brand-primary px-2 py-0.5 rounded text-[10px]">矢量重构中</span>
            </div>

            <!-- CAD Preview -->
            <div class="relative h-[340px] bg-[#06070a] rounded-xl mt-3 p-3 flex items-center justify-center overflow-hidden border border-white/5">
              <svg class="w-full h-full text-brand-primary/90" viewBox="0 0 400 400">
                <!-- Grid -->
                <g stroke="#1a202c" stroke-width="0.8">
                  <line x1="0" y1="50" x2="400" y2="50"/>
                  <line x1="0" y1="100" x2="400" y2="100"/>
                  <line x1="0" y1="150" x2="400" y2="150"/>
                  <line x1="0" y1="200" x2="400" y2="200"/>
                  <line x1="0" y1="250" x2="400" y2="250"/>
                  <line x1="0" y1="300" x2="400" y2="300"/>
                  <line x1="0" y1="350" x2="400" y2="350"/>
                  <line x1="200" y1="0" x2="200" y2="400"/>
                </g>

                <!-- Pattern Paths -->
                <path :d="patternPath" fill="none" stroke="#ffab00" stroke-width="2" class="transition-all duration-700"/>
                <path d="M 200,60 L 260,60 L 310,120 L 300,220 L 200,360" fill="none" stroke="#8b5cf6" stroke-width="1.5" stroke-dasharray="4,2"/>
                <path d="M 140,60 L 110,120" stroke="#f43f5e" stroke-width="1.5" stroke-dasharray="2,2"/>
                <circle cx="140" cy="60" r="4" fill="#ffab00" class="animate-ping"/>
                <circle cx="140" cy="60" r="3" fill="#ffffff"/>
                <circle cx="200" cy="60" r="3" fill="#ffffff"/>
                <circle cx="110" cy="120" r="3" fill="#ffffff"/>
                <circle cx="80" cy="220" r="3" fill="#ffffff"/>

                <!-- Dimension Labels -->
                <text x="145" y="45" fill="#e2e8f0" font-size="10" font-family="monospace">肩宽: 42.5cm</text>
                <text x="205" y="210" fill="#ffab00" font-size="10" font-family="monospace">胸省腰点: +2.8cm</text>
                <text x="95" y="380" fill="#38bdf8" font-size="10" font-family="monospace">总衣长: 74.0cm</text>
              </svg>

              <!-- AI Floating Tag -->
              <div class="absolute top-4 right-4 glass-card px-3 py-1.5 rounded-lg border border-purple-500/30 text-[11px] font-mono text-purple-300 flex items-center space-x-2">
                <Cpu class="w-3.5 h-3.5 text-purple-400" />
                <span>省道角度自动匹配: 18.4°</span>
              </div>
            </div>

            <!-- Bottom Controls -->
            <div class="flex items-center justify-between mt-3 px-2 text-xs">
              <span class="text-gray-400">状态: <span class="text-emerald-400 font-mono">100% 工业可缝合</span></span>
              <button @click="togglePattern" class="text-brand-primary hover:text-amber-300 font-mono flex items-center space-x-1">
                <span>{{ isSuit ? '切换女性修身版型' : '切换男性直筒版型' }}</span>
                <RefreshCw class="w-3 h-3" />
              </button>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>
