<template>
  <div ref="selectRef" class="win-select">
    <div ref="referenceRef" class="win-select__input" @click="onShow">反对东方东方东方的</div>
    <ul v-show="show" ref="popperRef" class="win-select__popper">
      <li class="win-select__item">森三扽发动</li>
      <li class="win-select__item">森三扽发动</li>
    </ul>
  </div>
</template>
<script setup lang="ts">
import { onMounted, ref, useTemplateRef } from 'vue'
import { createPopper } from '@popperjs/core';
import { onClickOutside } from '@vueuse/core'
import type { Instance } from '@popperjs/core';

let popperInstance: Instance | null
const selectRef = useTemplateRef('selectRef')
const referenceRef = useTemplateRef('referenceRef')
const popperRef = useTemplateRef('popperRef')
const show = ref(false)

onClickOutside(selectRef, () => {
  show.value = false
})

const onShow = () => {
  show.value = true
  popperInstance?.update()
}

onMounted(() => {
  popperRef.value!.style.width = referenceRef.value!.offsetWidth + 'px'
  popperInstance = createPopper(referenceRef.value as Element, popperRef.value as HTMLElement, {
    modifiers: [
      {
        name: 'offset',
        options: {
          offset: [0, -30],
        },
      },
    ],
  })
})
</script>

<style lang="scss" scoped>
.win-select {
  cursor: pointer;
  user-select: none;
}

.win-select__input {
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
  transition: background-color 0.1s ease-in-out;
  background-color: var(--win-select-bg-color);
  padding: var(--win-select-padding);
  border-radius: var(--win-select-border-radius);

  &:hover {
    background-color: var(--win-select-bg-color-hover);
  }
}

.win-select__popper {
  background-color: #d6d6d6;
  border-radius: 8px;
  padding: 4px 4px;
  display: flex;
  flex-direction: column;
  gap: 4px;
  color: #333;
  box-sizing: border-box;
  box-shadow: 0 3px 5px rgba(0, 0, 0, 0.2);
}

.win-select__item {
  padding: 8px 12px;
  border-radius: 4px;

  &:hover {
    background-color: #cecece;
  }
}
</style>