<script setup lang="ts">
import { ref } from 'vue'
import { Sparkles, CheckCircle, Download, Send } from 'lucide-vue-next'

const inputText = ref('')
</script>

<template>
  <section id="ai-pattern" class="py-20 border-b border-dark-border bg-dark-bg relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center max-w-3xl mx-auto mb-12">
        <span class="bg-gradient-to-r from-indigo-500 to-purple-600 text-white text-xs px-3 py-1 rounded-full font-bold uppercase tracking-widest shadow-lg shadow-purple-500/30">
          AI ASSISTANT PRO
        </span>
        <h2 class="text-3xl sm:text-4xl font-bold text-white mt-4">对话即制版 · 智能自动推码</h2>
        <p class="text-gray-400 text-sm mt-3">深度训练了千万张高定大牌图纸，支持自然语言输入 Prompt 快速生成工业级样板。</p>
      </div>

      <!-- AI Console -->
      <div class="max-w-4xl mx-auto glass-card rounded-2xl overflow-hidden shadow-2xl border border-purple-500/20">
        <!-- Console Header -->
        <div class="bg-dark-card px-6 py-3.5 border-b border-dark-border flex items-center justify-between">
          <div class="flex items-center space-x-2">
            <div class="w-3 h-3 rounded-full bg-red-500"></div>
            <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
            <div class="w-3 h-3 rounded-full bg-green-500"></div>
            <span class="ml-2 text-xs text-gray-300 font-mono">Pattern AI Console v3.5 - High Precision</span>
          </div>
          <span class="text-xs text-purple-400 flex items-center space-x-1 font-mono">
            <Sparkles class="w-3.5 h-3.5" />
            <span>GPT-4o Pattern Engine</span>
          </span>
        </div>

        <!-- Chat Area -->
        <div class="p-6 space-y-6">
          <!-- User Message -->
          <div class="flex items-start space-x-3">
            <div class="w-9 h-9 rounded-full bg-brand-primary text-black flex items-center justify-center font-bold text-xs flex-shrink-0 shadow-md">
              You
            </div>
            <div class="bg-dark-hover border border-white/10 p-4 rounded-2xl rounded-tl-none text-sm text-gray-200 max-w-xl">
              生成一款2026早春修身女式双排扣小西装样板，枪驳领宽8cm，带腰省，并根据S/M/L码生成嵌套推码图。
            </div>
          </div>

          <!-- AI Response -->
          <div class="flex items-start space-x-3">
            <div class="w-9 h-9 rounded-full bg-gradient-to-r from-indigo-500 to-purple-600 text-white flex items-center justify-center font-bold text-xs flex-shrink-0 shadow-md">
              AI
            </div>
            <div class="bg-dark-bg border border-purple-500/30 p-5 rounded-2xl rounded-tl-none text-sm space-y-4 w-full">
              <div class="flex items-center justify-between text-xs text-purple-300 border-b border-purple-500/20 pb-3">
                <span>已解析需求：女式双排扣西装 (包含 S, M, L 3个规格)</span>
                <span class="text-emerald-400 flex items-center space-x-1">
                  <CheckCircle class="w-3.5 h-3.5" />
                  <span>生成完毕 (耗时 0.6s)</span>
                </span>
              </div>

              <!-- Data Cards -->
              <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 text-xs font-mono">
                <div class="bg-dark-card p-3 rounded-lg border border-white/5">
                  <span class="text-gray-400 block mb-1">基准规格 (M码)</span>
                  <span class="text-white font-bold">胸围: 88cm | 肩宽: 38cm</span>
                </div>
                <div class="bg-dark-card p-3 rounded-lg border border-white/5">
                  <span class="text-gray-400 block mb-1">领型算力标定</span>
                  <span class="text-white font-bold">驳角: 42° | 领宽: 8.0cm</span>
                </div>
                <div class="bg-dark-card p-3 rounded-lg border border-white/5">
                  <span class="text-gray-400 block mb-1">推码档差 (Grading)</span>
                  <span class="text-purple-400 font-bold">围度档差: 4.0cm / 码</span>
                </div>
              </div>

              <!-- Nested Pattern SVG -->
              <div class="h-36 bg-dark-bg border border-dark-border rounded-xl flex items-center justify-center relative overflow-hidden">
                <svg class="w-72 h-full text-purple-400 opacity-90" viewBox="0 0 200 100">
                  <!-- S -->
                  <path d="M40,20 L80,20 L75,80 L45,80 Z" fill="none" stroke="currentColor" stroke-width="0.8" stroke-dasharray="2,2"/>
                  <!-- M -->
                  <path d="M38,18 L82,18 L77,82 L43,82 Z" fill="none" stroke="#ffab00" stroke-width="1.5"/>
                  <!-- L -->
                  <path d="M36,16 L84,16 L79,84 L41,84 Z" fill="none" stroke="currentColor" stroke-width="0.8" stroke-dasharray="2,2"/>
                </svg>
                <span class="absolute bottom-2 right-3 text-[10px] text-gray-400 bg-black/70 px-2 py-0.5 rounded font-mono">S/M/L 三码嵌套视图</span>
              </div>

              <!-- Action Buttons -->
              <div class="flex space-x-3 pt-1">
                <button class="px-5 py-2.5 bg-gradient-to-r from-indigo-500 to-purple-600 hover:opacity-90 text-white text-xs font-semibold rounded-lg transition flex items-center space-x-1.5 shadow-md">
                  <Download class="w-4 h-4" />
                  <span>导出 DXF 格式源文件</span>
                </button>
                <button class="px-5 py-2.5 glass-card hover:bg-dark-hover text-gray-300 text-xs font-semibold rounded-lg transition border border-white/10">
                  在 Web CAD 编辑器中打开
                </button>
              </div>
            </div>
          </div>
        </div>

        <!-- Input Bar -->
        <div class="bg-dark-card p-4 border-t border-dark-border flex items-center space-x-3">
          <input
            v-model="inputText"
            type="text"
            placeholder="输入修改要求，如：'将衣长延长 4cm，并将领型修改为平驳领'..."
            class="flex-1 bg-dark-bg border border-white/10 text-xs text-white rounded-xl px-4 py-3 focus:outline-none focus:border-purple-500"
          >
          <button class="bg-gradient-to-r from-indigo-500 to-purple-600 text-white p-3 rounded-xl hover:opacity-90 transition">
            <Send class="w-4 h-4" />
          </button>
        </div>
      </div>
    </div>
  </section>
</template>
