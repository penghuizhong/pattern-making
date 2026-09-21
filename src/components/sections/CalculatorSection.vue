<script setup lang="ts">
import { ref, computed } from 'vue'
import { Calculator, CheckCircle2, Sliders, Copy } from 'lucide-vue-next'

const bust = ref(88)
const length = ref(68)
const ease = ref(6)

const armhole = computed(() => (bust.value / 6 + 7).toFixed(2))
const neck = computed(() => (bust.value / 20 + 2.9).toFixed(2))
const chest = computed(() => (bust.value / 6 + 3).toFixed(2))
const back = computed(() => (bust.value / 6 + 4.5).toFixed(2))
</script>

<template>
  <section id="calculator" class="py-20 border-b border-dark-border">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">

        <!-- Left Description -->
        <div class="lg:col-span-5 space-y-6">
          <div class="inline-flex items-center space-x-2 text-brand-primary font-mono text-xs">
            <Calculator class="w-4 h-4" />
            <span>SMART FORMULA CALCULATOR</span>
          </div>
          <h2 class="text-3xl sm:text-4xl font-bold text-white leading-tight">
            服装打版智能公式计算器
          </h2>
          <p class="text-gray-400 text-sm leading-relaxed">
            摆脱繁琐的手工代入公式。只需滑动设定胸围、衣长与放松量，系统自动按照日本文化式/美式文化式/国标GB计算领宽、袖深及关键节点坐标。
          </p>

          <ul class="space-y-3 text-xs text-gray-300">
            <li class="flex items-center space-x-2.5">
              <CheckCircle2 class="w-4 h-4 text-emerald-400 flex-shrink-0" />
              <span>实时计算 B/6 + 7cm 等多种工业公差</span>
            </li>
            <li class="flex items-center space-x-2.5">
              <CheckCircle2 class="w-4 h-4 text-emerald-400 flex-shrink-0" />
              <span>包含缝裕 (Seam Allowance) 自动缩水率补偿</span>
            </li>
            <li class="flex items-center space-x-2.5">
              <CheckCircle2 class="w-4 h-4 text-emerald-400 flex-shrink-0" />
              <span>一键复制导出变量文本，直接导入 CAD 软件</span>
            </li>
          </ul>
        </div>

        <!-- Right Calculator Panel -->
        <div class="lg:col-span-7 glass-card p-6 sm:p-8 rounded-2xl shadow-2xl border border-dark-border">
          <div class="flex items-center justify-between pb-4 border-b border-dark-border">
            <span class="text-white font-semibold flex items-center space-x-2">
              <Sliders class="w-4 h-4 text-brand-primary" />
              <span>原型尺寸推算演示 (原型 B 算法)</span>
            </span>
            <span class="text-xs text-gray-400 font-mono">规范: 文化式 8代体系</span>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-6">
            <!-- Input Sliders -->
            <div class="space-y-5">
              <div>
                <div class="flex justify-between text-xs text-gray-300 mb-2">
                  <label class="font-medium">净胸围 (Bust):</label>
                  <span class="font-mono text-brand-primary font-bold">{{ bust }} cm</span>
                </div>
                <input type="range" v-model.number="bust" min="70" max="120" class="w-full">
              </div>

              <div>
                <div class="flex justify-between text-xs text-gray-300 mb-2">
                  <label class="font-medium">衣长 (Length):</label>
                  <span class="font-mono text-brand-primary font-bold">{{ length }} cm</span>
                </div>
                <input type="range" v-model.number="length" min="50" max="100" class="w-full">
              </div>

              <div>
                <div class="flex justify-between text-xs text-gray-300 mb-2">
                  <label class="font-medium">放松量 (Ease):</label>
                  <span class="font-mono text-brand-primary font-bold">{{ ease }} cm</span>
                </div>
                <input type="range" v-model.number="ease" min="0" max="20" class="w-full">
              </div>
            </div>

            <!-- Results -->
            <div class="bg-dark-bg border border-dark-border rounded-xl p-4 space-y-3 font-mono">
              <div class="text-xs text-gray-400 border-b border-dark-border pb-2 flex justify-between">
                <span>结构部位</span>
                <span>实时推算数值</span>
              </div>

              <div class="flex justify-between items-center text-xs">
                <span class="text-gray-300">袖深 (B/6 + 7cm):</span>
                <span class="text-brand-primary font-bold">{{ armhole }} cm</span>
              </div>

              <div class="flex justify-between items-center text-xs">
                <span class="text-gray-300">领宽 (B/20 + 2.9cm):</span>
                <span class="text-brand-primary font-bold">{{ neck }} cm</span>
              </div>

              <div class="flex justify-between items-center text-xs">
                <span class="text-gray-300">前胸宽 (B/6 + 3cm):</span>
                <span class="text-emerald-400 font-bold">{{ chest }} cm</span>
              </div>

              <div class="flex justify-between items-center text-xs">
                <span class="text-gray-300">后背宽 (B/6 + 4.5cm):</span>
                <span class="text-emerald-400 font-bold">{{ back }} cm</span>
              </div>

              <div class="pt-3">
                <button class="w-full py-2.5 bg-brand-primary/10 hover:bg-brand-primary/20 border border-brand-primary/40 text-brand-primary text-xs font-semibold rounded-lg transition font-sans flex items-center justify-center space-x-1">
                  <Copy class="w-3.5 h-3.5" />
                  <span>复制参数至 CAD 剪贴板</span>
                </button>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>
