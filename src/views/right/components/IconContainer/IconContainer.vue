<script setup>
import IconItem from "@/views/right/components/IconContainer/components/IconItem.vue";
import {ref} from "vue";

const iconItems = ref([{
  icon: 'GitHub',
  label: 'GitHub'
}, {
  icon: 'QQ',
  label: 'QQ音乐'
}, {
  icon: 'Wyy',
  label: '网易云音乐'
}])
</script>

<template>
  <div class="icon-container">
    <IconItem v-for="item in iconItems" :key="item.label" :label="item.label" :icon="item.icon"/>
  </div>
</template>

<style scoped>
.icon-container {
  margin: 10px 0;
  display: flex;
}
</style>