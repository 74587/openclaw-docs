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
      <!-- 宽屏：728×90 -->
      <picture class="tc-ad-img tc-ad-img--wide">
        <source :srcset="wideWebp" type="image/webp" />
        <img
          :src="widePng"
          alt="腾讯云特惠活动 · 云服务器、数据库、CDN 新用户专享折扣"
          width="728"
          height="90"
          loading="lazy"
          @error="onError"
        />
      </picture>
      <!-- 移动端：300×250 -->
      <picture class="tc-ad-img tc-ad-img--narrow">
        <source :srcset="narrowWebp" type="image/webp" />
        <img
          :src="narrowPng"
          alt="腾讯云特惠活动 · 云服务器、数据库、CDN 新用户专享折扣"
          width="300"
          height="250"
          loading="lazy"
          @error="onError"
        />
      </picture>
    </a>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const wideWebp  = '/assets/cloud/tc-728x90.webp'
const widePng   = '/assets/cloud/tc-728x90.png'
const narrowWebp = '/assets/cloud/tc-300x250.webp'
const narrowPng  = '/assets/cloud/tc-300x250.png'

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
}

.tc-ad-img img {
  max-width: 100%;
  height: auto;
  border-radius: 6px;
  display: block;
}

.tc-ad-img--wide   { display: inline-block; }
.tc-ad-img--narrow { display: none; }

@media (max-width: 768px) {
  .tc-ad-img--wide   { display: none; }
  .tc-ad-img--narrow { display: inline-block; }
}
</style>
