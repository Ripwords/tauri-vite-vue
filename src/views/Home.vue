<script lang="ts" setup>
import { mainStore } from "../store/pinia";
import { ref } from "vue";

defineEmits(['changeTheme'])

const store = mainStore()
const theme = ref("dark")
const changeIcon = () => {
  if (theme.value === "dark") {
    theme.value = "light"
  } else {
    theme.value = "dark"
  }
}
</script>

<template>
  <n-h1 class="center" style="margin-top: 25px;">Hello {{ store.dec }}</n-h1>
  <div class="center">
    <n-button @click="store.dec++">Increment</n-button>
    <n-button @click="store.dec--">Decrease</n-button>
  </div>
  <div class="center">
    <n-button @click="$emit('changeTheme'); changeIcon()">
      <i-akar-icons:moon-fill v-if="theme == 'dark'"></i-akar-icons:moon-fill>
      <i-akar-icons:sun-fill v-if="theme == 'light'"></i-akar-icons:sun-fill>
    </n-button>
  </div>
</template>

<style scoped>
.center {
  display: flex;
  justify-content: center;
}
</style>