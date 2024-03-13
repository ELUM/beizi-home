<script setup>
import {onMounted, ref} from "vue";

const props = defineProps({
  label: {
    type: String,
    default: () => ''
  },
  icon: {
    type: String,
    default: () => ''
  }
})
const stringWidth = ref()
onMounted(() => {
  hasStringLanguage(props.label)
})
const hasStringLanguage = (val) => {
  let sum = 0
  for (let valElement of val) {
    // 判断是否为中文
    let pattern = new RegExp("[\u4E00-\u9FA5]+");
    if (pattern.test(valElement)) {
      sum = sum + 16
    }

    // 判断是否为英文
    let pattern2 = new RegExp("[A-Za-z]+");
    if (pattern2.test(valElement)) {
      sum = sum + 12
    }

    // 判断是否为数字
    let pattern3 = new RegExp("[0-9]+");
    if (pattern3.test(valElement)) {
      sum = sum + 8
    }
  }
  stringWidth.value = `${sum}px`
}
</script>

<template>
  <div class="icon-item">
    <span class="icon">{{ props.icon }}</span>
    <span class="label">{{ props.label }}</span>
  </div>
</template>

<style scoped>
.icon-item {
  text-align: center;
  width: 50px;
  height: 38px;
  background-color: aqua;
  padding: 3px;
  transition: width .3s ease;
  border-radius: 3px;
  margin-right: 10px;
  overflow: hidden;
}
.icon-item >
.label {
  display: none;
}

.icon-item:hover {
  width: v-bind(stringWidth);
}

.icon-item:hover > .label {
  display: inline;
}

</style>