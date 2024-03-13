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
  setIconWeightByStringType(props.label)
})

// 根据字符类型设置icon的宽度
const setIconWeightByStringType = (val) => {
  let sum = 0
  for (let valElement of val) {
    // 判断是否为中文
    let pattern = new RegExp("[\u4E00-\u9FA5]+");
    if (pattern.test(valElement)) {
      sum = sum + 24
    }

    // 判断是否为英文
    let capital = new RegExp("[A-Z]+");
    if (capital.test(valElement)) {
      sum = sum + 24
    }

    let lower = new RegExp("[a-z]+")
    if (lower.test(valElement)) {
      sum = sum + 16
    }

    // 判断是否为数字
    let pattern3 = new RegExp("[0-9]+");
    if (pattern3.test(valElement)) {
      sum = sum + 10
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
  padding: 0 3px;
  width: 80px;
  height: 38px;
  line-height: 38px;
  transition: width .3s ease;
  border-radius: 3px;
  margin-right: 10px;
  overflow: hidden;
  position: relative;
}

.icon-item:before {
  content: " ";
  width: 100%;
  height: 38px;
  background: inherit;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  box-shadow: inset 0 0 0 200px rgba(255, 255, 255, 0.25);
  backdrop-filter: blur(10px);
  z-index: -1;
}

.icon-item > .label {
  display: none;
}

.icon-item:hover {
  width: v-bind(stringWidth);
}

.icon-item:hover > .label {
  display: inline;
}

</style>