<template>
  <div v-if="visible" class="tc-ad-wrap">
    <p class="tc-ad-label">广告 · 本站推荐</p>
    <a
      href="https://curl.qcloud.com/EWbhzkIl"
      target="_blank"
      rel="noopener sponsored"
      class="tc-ad-link"
      aria-label="腾讯云特惠活动"
    >
      <img
        :src="wideSrc"
        alt="腾讯云特惠活动 · 云服务器、数据库、CDN 新用户专享折扣"
        class="tc-ad-img tc-ad-img--wide"
        width="728"
        height="90"
        loading="lazy"
        @error="onError"
      />
      <img
        :src="narrowSrc"
        alt="腾讯云特惠活动 · 云服务器、数据库、CDN 新用户专享折扣"
        class="tc-ad-img tc-ad-img--narrow"
        width="300"
        height="250"
        loading="lazy"
        @error="onError"
      />
    </a>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// 用变量绑定而非静态 src，阻止 Vite 将图片转为模块 import
// 广告拦截器只会拦截 HTTP 请求，不会导致模块崩溃
const wideSrc = '/assets/cloud/tc-728x90.png'
const narrowSrc = '/assets/cloud/tc-300x250.png'

const visible = ref(true)
let errorCount = 0

function onError() {
  errorCount++
  if (errorCount >= 2) visible.value = false
}
</script>

<style scoped>
.tc-ad-wrap {
  margin-top: 0;
  margin-bottom: 1.5rem;
  padding-top: 0;
  border-top: none;
  text-align: center;
}

.tc-ad-label {
  font-size: 0.72rem;
  color: var(--vp-c-text-3);
  margin-bottom: 0.5rem;
  letter-spacing: 0.05em;
}

.tc-ad-link {
  display: inline-block;
  line-height: 0;
}

.tc-ad-img {
  max-width: 100%;
  height: auto;
  border-radius: 6px;
}

.tc-ad-img--wide   { display: inline-block; }
.tc-ad-img--narrow { display: none; }

@media (max-width: 768px) {
  .tc-ad-img--wide   { display: none; }
  .tc-ad-img--narrow { display: inline-block; }
}
</style>
