<script setup lang="ts">
import { ref } from 'vue'

const email = ref('')
</script>

<template>
  <footer class="footer-section bg-dark-bg py-12 border-t border-dark-border text-xs">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-8 mb-12">

        <!-- Brand -->
        <div class="space-y-4">
          <div class="flex items-center space-x-3">
            <div class="w-8 h-8 border border-white rounded-lg flex items-center justify-center">
              <div class="w-2.5 h-2.5 bg-white rounded-full"></div>
            </div>
            <span class="text-lg font-bold text-white tracking-wider">方圆智版</span>
          </div>
          <p class="text-gray-500 leading-relaxed">
            AI 服装智能制版平台。用先进算法融合高级时装结构，打造工业级服装制版与推码引擎。
          </p>
        </div>

        <!-- Product Links -->
        <div>
          <h4 class="text-xs font-bold text-white uppercase tracking-wider mb-4">产品功能</h4>
          <ul class="space-y-2.5">
            <li><a href="#ai-assistant" class="hover:text-brand-primary transition">AI 智能打版引擎</a></li>
            <li><a href="#calculator" class="hover:text-brand-primary transition">智能原型公式计算器</a></li>
            <li><a href="#cad-library" class="hover:text-brand-primary transition">矢量 CAD 图稿库</a></li>
            <li><a href="#ai-assistant" class="hover:text-brand-primary transition">自动推码 (Grading) 系统</a></li>
          </ul>
        </div>

        <!-- Learning Links -->
        <div>
          <h4 class="text-xs font-bold text-white uppercase tracking-wider mb-4">学习资源</h4>
          <ul class="space-y-2.5">
            <li><a href="#tutorials" class="hover:text-brand-primary transition">制版教学中心</a></li>
            <li><a href="#knowledge" class="hover:text-brand-primary transition">服装结构知识库</a></li>
            <li><a href="javascript:void(0)" class="hover:text-brand-primary transition">开发者 API</a></li>
            <li><a href="javascript:void(0)" class="hover:text-brand-primary transition">更新日志</a></li>
          </ul>
        </div>

        <!-- Newsletter -->
        <div>
          <h4 class="text-xs font-bold text-white uppercase tracking-wider mb-4">获取最新资讯</h4>
          <p class="text-gray-500 mb-3">订阅邮件，第一时间获取 AI 新版型发布与算法更新。</p>
          <div class="flex items-center">
            <input
              v-model="email"
              type="email"
              placeholder="您的电子邮箱"
              class="bg-dark-card border border-dark-border px-3 py-2 rounded-l-lg text-white focus:outline-none focus:border-brand-primary w-full"
            >
            <button class="bg-brand-primary text-black font-bold px-4 py-2 rounded-r-lg hover:bg-amber-400 transition flex-shrink-0">订阅</button>
          </div>
        </div>

      </div>

      <div class="border-t border-dark-border pt-6 flex flex-col sm:flex-row items-center justify-between text-gray-500">
        <p>&copy; 2026 方圆智版 (AI 服装智能制版) 保留所有权利。</p>
        <div class="flex space-x-6 mt-4 sm:mt-0">
          <a href="javascript:void(0)" class="hover:text-gray-300 transition">隐私政策</a>
          <a href="javascript:void(0)" class="hover:text-gray-300 transition">服务条款</a>
          <a href="javascript:void(0)" class="hover:text-gray-300 transition">沪ICP备XXXXXX号</a>
        </div>
      </div>
    </div>
  </footer>
</template>
