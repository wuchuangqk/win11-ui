<template>
  <div>
    <!-- 显示区域 -->
    <div class="win-menu-item">
      <div>
        <div class="win-menu-item__title">{{ title }}</div>
        <div v-if="description" class="win-menu-item__description">{{ description }}</div>
      </div>
      <div>
        <slot></slot>
      </div>
    </div>
    <!-- 折叠区域 -->
    <div></div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'

const {
  title,
  description = '',
} = defineProps<{
  title: string
  description?: string
}>()
</script>

<style lang="scss" scoped>
.win-menu-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--win-menu-item-padding);
  border-radius: var(--win-menu-item-border-radius);
  background-color: var(--win-menu-item-bg-color);
}

.win-menu-item__title {
  color: var(--win-color);
}

.win-menu-item__description {
  margin-top: 4px;
  color: var(--win-sub-color);
  font-size: var(--win-font-size-sub);
}
</style>