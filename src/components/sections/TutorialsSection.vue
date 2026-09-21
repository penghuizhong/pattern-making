<script setup lang="ts">
import { GraduationCap, ArrowRight } from 'lucide-vue-next'

const tutorials = [
  {
    image: 'https://images.unsplash.com/photo-1558769132-cb1aea458c5e?auto=format&fit=crop&w=800&q=80',
    badge: '4K 视频教程',
    badgeColor: 'text-brand-primary',
    level: '基础与进阶',
    levelColor: 'text-brand-primary',
    title: '女装原型立体裁剪与平面打版转换',
    desc: '剖析人体曲面与胸省转移原理，掌握各类复杂领型与袖型的公式微调。',
    hours: '12 课时 · 4.8 小时',
    price: '免费观看',
    priceColor: 'text-emerald-400',
    hoverTitle: 'group-hover:text-brand-primary',
  },
  {
    image: 'https://images.unsplash.com/photo-1537832816519-689ad163238b?auto=format&fit=crop&w=800&q=80',
    badge: '高定大师课',
    badgeColor: 'text-purple-400',
    level: '大师专精',
    levelColor: 'text-purple-400',
    title: '萨维尔街传统男士西装高定打版精讲',
    desc: '经典双排扣西装结构拆解，包含胸衬归拔工艺数字化实战。',
    hours: '18 课时 · 8.2 小时',
    price: 'PRO 专享',
    priceColor: 'text-brand-primary',
    hoverTitle: 'group-hover:text-purple-400',
  },
  {
    image: 'https://images.unsplash.com/photo-1520006403909-838d6b92c22e?auto=format&fit=crop&w=800&q=80',
    badge: '工业实战',
    badgeColor: 'text-emerald-400',
    level: '工业自动化',
    levelColor: 'text-emerald-400',
    title: 'AI 驱动下工业级批量自动推码与排料',
    desc: '利用方圆智版 AI 引擎完成高效率自动推码及面料利用率最大化实操。',
    hours: '8 课时 · 3.5 小时',
    price: '免费观看',
    priceColor: 'text-emerald-400',
    hoverTitle: 'group-hover:text-emerald-400',
  },
]
</script>

<template>
  <section id="tutorials" class="py-20 border-b border-dark-border">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between mb-12">
        <div>
          <div class="text-brand-primary text-xs font-mono mb-2 flex items-center space-x-1">
            <GraduationCap class="w-4 h-4" />
            <span>KNOWLEDGE & TUTORIALS</span>
          </div>
          <h2 class="text-3xl sm:text-4xl font-bold text-white">
            制版知识库与教学课程
          </h2>
          <p class="text-gray-400 text-sm mt-1">从传统手工立裁打版到 AI 智能化数控打版的全套进阶指导</p>
        </div>
        <a href="javascript:void(0)" class="hidden sm:flex text-xs text-brand-primary hover:underline items-center space-x-1 font-semibold">
          <span>浏览全部教程</span>
          <ArrowRight class="w-3.5 h-3.5" />
        </a>
      </div>

      <div id="knowledge" class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div
          v-for="t in tutorials"
          :key="t.title"
          class="glass-card rounded-2xl overflow-hidden border border-dark-border hover:border-gray-500 transition group"
        >
          <div class="h-48 bg-gray-800 relative overflow-hidden">
            <img :src="t.image" :alt="t.title" class="w-full h-full object-cover group-hover:scale-105 transition duration-500 opacity-70">
            <span class="absolute top-3 left-3 bg-black/80 backdrop-blur text-[10px] px-2.5 py-1 rounded font-mono font-bold" :class="t.badgeColor">{{ t.badge }}</span>
          </div>
          <div class="p-6">
            <div class="text-xs font-mono mb-2" :class="t.levelColor">{{ t.level }}</div>
            <h3 class="text-white font-bold text-base transition" :class="t.hoverTitle">{{ t.title }}</h3>
            <p class="text-gray-400 text-xs mt-2 leading-relaxed line-clamp-2">{{ t.desc }}</p>
            <div class="flex items-center justify-between mt-6 pt-4 border-t border-dark-border text-xs text-gray-500">
              <span>{{ t.hours }}</span>
              <span class="font-semibold" :class="t.priceColor">{{ t.price }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
