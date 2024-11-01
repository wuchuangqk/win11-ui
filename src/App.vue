<template>
  <div :class="theme">
    <div>
      theme:
      <input type="radio" id="dark" name="theme" value="theme-dark" checked v-model="theme" />
      <label for="dark">dark</label>
      <input type="radio" id="light" name="theme" value="theme-light" v-model="theme" />
      <label for="light">light</label>
    </div>
    <Menu title="启动">
      <Collapse title="默认配置文件" description="单击'+'图标或通过键入绑定时打开的配置文件。">
        <Select></Select>
      </Collapse>
      <Collapse title="在计算机启动时启动" description="登录到windows时自动启动终端">
        <Select></Select>
      </Collapse>
    </Menu>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Collapse from './components/collapse/collapse.vue';
import Select from './components/select/select.vue';
import Menu from './components/menu/menu.vue';

const theme = ref('theme-dark')
</script>
