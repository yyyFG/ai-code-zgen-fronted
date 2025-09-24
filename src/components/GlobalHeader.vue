<template>
  <a-layout-header class="global-header">
    <div class="header-inner">
      <div class="brand" @click="goHome">
        <img class="logo" src="/favicon.svg" alt="logo" />
        <span class="title">代码生成共享平台</span>
      </div>

      <a-menu class="nav-menu" mode="horizontal" theme="dark" :selectedKeys="selectedKeys">
        <a-menu-item v-for="item in menuItems" :key="item.key">
          <RouterLink :to="item.path">{{ item.label }}</RouterLink>
        </a-menu-item>
      </a-menu>

      <div class="actions">
        <a-button type="primary">登录</a-button>
      </div>
    </div>
  </a-layout-header>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { useRoute, useRouter } from 'vue-router'

interface MenuItemConfig {
  key: string
  label: string
  path: string
}

const router = useRouter()
const route = useRoute()

const menuItems: MenuItemConfig[] = [
  { key: 'home', label: '首页', path: '/' },
  { key: 'about', label: '关于', path: '/about' },
]

const selectedKeys = computed(() => {
  const found = menuItems.find((m) => route.path.startsWith(m.path))
  return found ? [found.key] : []
})

function goHome() {
  router.push('/')
}
</script>
<script lang="ts">
export default { name: 'GlobalHeader' }
</script>

<style scoped>
.global-header {
  display: flex;
  align-items: center;
  padding: 0;
}

.header-inner {
  display: flex;
  align-items: center;
  gap: 16px;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}

.brand {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
}

.logo {
  width: 28px;
  height: 28px;
}

.title {
  color: #fff;
  font-size: 16px;
  font-weight: 600;
}

.nav-menu {
  flex: 1;
  min-width: 0;
}

.actions {
  display: flex;
  align-items: center;
}

@media (max-width: 768px) {
  .title {
    display: none;
  }
}
</style>
