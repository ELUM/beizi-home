<script setup>
import {ref} from "vue";
import IconContainer from "@/views/right/components/IconContainer/IconContainer.vue";

const descriptions = ref([
  '😅 一个自言自语的话',
  '😂 TMD不想奋斗了',
])
</script>

<template>
  <header>
    <div class="welcome">Hello,I'm XXX</div>
    <div class="description" v-for="item in descriptions" :key="item">{{ item }}</div>
    <IconContainer/>
  </header>
</template>

<style scoped>
.welcome {
  font-size: 55px;
  font-weight: 800;
}

.description {
  font-size: 20px;
  margin-top: 7px;
}
</style>