<template>
  <a-layout class="basic-layout">
    <GlobalHeader />
    <a-layout-content class="layout-content">
      <router-view />
    </a-layout-content>
    <GlobalFooter />
  </a-layout>
</template>

<script setup lang="ts">
import GlobalHeader from '../components/GlobalHeader.vue'
import GlobalFooter from '../components/GlobalFooter.vue'
</script>
<script lang="ts">
export default { name: 'BasicLayout' }
</script>

<style scoped>
.basic-layout {
  min-height: 100vh;
  background: #f5f5f5;
}

.layout-content {
  padding: 16px;
  margin: 0 auto;
  width: 100%;
  max-width: 1200px;
}

@media (max-width: 768px) {
  .layout-content {
    padding: 12px;
  }
}
</style>
