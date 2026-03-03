<template>
  <div v-if="visible" class="tc-ad-wrap">
    <p class="tc-ad-label">广告 · 本站推荐</p>
    <a
      href="https://curl.qcloud.com/3AjnOxhc"
      target="_blank"
      rel="noopener sponsored"
      class="tc-ad-link"
      aria-label="腾讯云特惠活动"
    >
      <img
        src="/assets/cloud/4e262771-f4a2-4302-920a-3bf136ace493.png"
        alt="腾讯云特惠活动 · 云服务器、数据库、CDN 新用户专享折扣"
        loading="lazy"
        class="tc-ad-img"
        @error="onError"
      />
    </a>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const visible = ref(true)

function onError() {
  visible.value = false
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
  display: block;
}
</style>
