<template>
  <div class="win-menu">
    <h1 class="win-menu__title">{{ title }}</h1>
    <div class="win-menu__wrapper">
      <slot></slot>
    </div>
  </div>
</template>
<script setup lang="ts">

const {
  title,
} = defineProps<{
  title: string
}>()
</script>

<style lang="scss" scoped>
.win-menu {
  padding: var(--win-menu-padding);
}

.win-menu__title {
  padding: var(--win-menu-title-padding);
}

.win-menu__wrapper {
  display: flex;
  flex-direction: column;
  gap: var(--win-menu-gap);
}
</style>