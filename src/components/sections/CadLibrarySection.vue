<script setup lang="ts">
import { ref } from 'vue'
import { Database, Download } from 'lucide-vue-next'

type CadCategory = 'all' | 'suit' | 'dress' | 'pants'

const activeFilter = ref<CadCategory>('all')

const filters: { key: CadCategory; label: string }[] = [
  { key: 'all', label: '全部版型' },
  { key: 'suit', label: '男士高级西装' },
  { key: 'dress', label: '女装与礼服' },
  { key: 'pants', label: '结构裤装' },
]

const cadItems = [
  {
    category: 'suit' as const,
    hoverColor: 'brand-primary',
    borderColor: 'hover:border-brand-primary/60',
    previewBorderColor: 'group-hover:border-brand-primary/30',
    svgColor: 'text-brand-primary/80',
    badge: 'DXF / PLT',
    badgeBg: 'bg-brand-primary/20 text-brand-primary',
    title: '意式双排扣枪驳领西服',
    desc: '三卡前片构造，精准归拔工艺线标注',
    downloads: '2,450',
    svgPath: 'M20,10 L80,10 L75,90 L25,90 Z M35,10 L50,40 L65,10 M50,40 L50,90',
    svgDash: 'stroke-dasharray="2,1"',
  },
  {
    category: 'dress' as const,
    hoverColor: 'purple-500',
    borderColor: 'hover:border-purple-500/60',
    previewBorderColor: 'group-hover:border-purple-500/30',
    svgColor: 'text-purple-400',
    badge: 'CAD 2025',
    badgeBg: 'bg-purple-500/20 text-purple-400',
    title: '法式高定赫本风连衣裙',
    desc: '高腰分割线条，内置立体鱼骨卡位',
    downloads: '4,120',
    svgPath: 'M30,10 Q50,20 70,10 L85,90 L15,90 Z',
    svgDash: '',
  },
  {
    category: 'pants' as const,
    hoverColor: 'emerald-500',
    borderColor: 'hover:border-emerald-500/60',
    previewBorderColor: 'group-hover:border-emerald-500/30',
    svgColor: 'text-emerald-400',
    badge: 'AI GRADED',
    badgeBg: 'bg-emerald-500/20 text-emerald-400',
    title: '经典双褶锥形绅士长裤',
    desc: '含立裆弧度自动优化，支持全码数推码',
    downloads: '1,890',
    svgPath: 'M25,10 L75,10 L85,90 L52,90 L50,30 L48,90 L15,90 Z',
    svgDash: '',
  },
  {
    category: 'suit' as const,
    hoverColor: 'amber-500',
    borderColor: 'hover:border-amber-500/60',
    previewBorderColor: 'group-hover:border-amber-500/30',
    svgColor: 'text-amber-400',
    badge: 'DXF / PDF',
    badgeBg: 'bg-amber-500/20 text-amber-400',
    title: '落肩廓形连帽卫衣原型',
    desc: '潮牌宽松剪裁，包含螺纹收口弹力比率',
    downloads: '3,200',
    svgPath: 'M10,20 L90,20 L80,85 L20,85 Z',
    svgDash: '',
    svgCircle: true,
  },
]

const filteredItems = ref(cadItems)

function setFilter(category: CadCategory) {
  activeFilter.value = category
  if (category === 'all') {
    filteredItems.value = cadItems
  } else {
    filteredItems.value = cadItems.filter(item => item.category === category)
  }
}
</script>

<template>
  <section id="cad-library" class="py-20 border-b border-dark-border bg-[#0a0c12]">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex flex-col md:flex-row md:items-end justify-between mb-12">
        <div>
          <div class="text-brand-primary text-xs font-mono mb-2 flex items-center space-x-1">
            <Database class="w-4 h-4" />
            <span>VECTOR CAD LIBRARY</span>
          </div>
          <h2 class="text-3xl sm:text-4xl font-bold text-white tracking-tight">
            高精度 CAD 板型图稿库
          </h2>
          <p class="text-gray-400 text-sm mt-2">涵盖男女装、高定礼服及休闲潮牌，支持全版本 DXF/PLT 矢量源文件一键下载</p>
        </div>

        <!-- Filter Buttons -->
        <div class="flex flex-wrap gap-2 mt-6 md:mt-0">
          <button
            v-for="f in filters"
            :key="f.key"
            :class="[
              activeFilter === f.key
                ? 'px-4 py-2 rounded-lg text-xs font-semibold bg-brand-primary text-black transition'
                : 'px-4 py-2 rounded-lg text-xs font-semibold glass-card text-gray-300 hover:text-white hover:border-gray-500 transition'
            ]"
            @click="setFilter(f.key)"
          >
            {{ f.label }}
          </button>
        </div>
      </div>

      <!-- CAD Cards -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
        <div
          v-for="item in filteredItems"
          :key="item.title"
          :class="['glass-card rounded-2xl p-4 transition-all duration-300 flex flex-col justify-between group', item.borderColor]"
        >
          <div>
            <div :class="['h-48 bg-[#050608] rounded-xl border border-white/5 flex items-center justify-center p-4 relative overflow-hidden transition', item.previewBorderColor]">
              <svg :class="['w-full h-full stroke-current fill-none', item.svgColor]" viewBox="0 0 100 100">
                <path :d="item.svgPath" :stroke-dasharray="item.svgDash || undefined" />
                <circle v-if="item.svgCircle" cx="50" cy="50" r="15" stroke-dasharray="2,2" />
              </svg>
              <span :class="['absolute top-3 right-3 text-[10px] px-2 py-0.5 rounded font-mono font-bold', item.badgeBg]">{{ item.badge }}</span>
            </div>
            <h3 :class="['font-semibold text-base mt-4 transition', `group-hover:text-${item.hoverColor}`]">{{ item.title }}</h3>
            <p class="text-gray-400 text-xs mt-1">{{ item.desc }}</p>
          </div>
          <div class="flex items-center justify-between pt-4 mt-4 border-t border-white/10 text-xs">
            <span class="text-gray-500">下载 {{ item.downloads }} 次</span>
            <a href="javascript:void(0)" class="text-brand-primary flex items-center space-x-1 hover:underline font-semibold">
              <span>下载矢量图</span>
              <Download class="w-3.5 h-3.5" />
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
