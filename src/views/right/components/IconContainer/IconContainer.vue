<script setup>
import IconItem from "@/views/right/components/IconContainer/components/IconItem.vue";
import {ref} from "vue";

const iconItems = ref([{
  icon: 'git',
  label: 'GitHub'
}, {
  icon: 'git',
  label: 'GitHu123213121121231b11'
}, {
  icon: 'git',
  label: '小胡小胡小胡小胡小胡小胡小胡小胡小胡小胡小胡小胡小胡小胡小胡小胡小胡'
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