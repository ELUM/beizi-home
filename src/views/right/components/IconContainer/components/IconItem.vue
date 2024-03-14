<script setup>
import {onMounted, ref} from "vue";
import {IconPark} from '@icon-park/vue-next/es/all';

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
      sum = sum + 12
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
    <icon-park style="height: 24px;width: 24px" type="github" theme="filled" size="24px" fill="#EEEEEE"/>
    <div class="label">{{ props.label }}</div>
  </div>
</template>

<style scoped>
.icon-item {
  gap: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 47px;
  height: 38px;
  transition: width .3s ease;
  border-radius: 3px;
  margin-right: 10px;
  position: relative;
  overflow: hidden;
}

.icon-item:before {
  content: " ";
  border-radius: 3px;
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

.icon-item:hover {
  overflow: hidden;
  background: rgba(255, 255, 255, 0.08);;
  width: v-bind(stringWidth);
}

.icon-item .label {
  display: none;
}

.icon-item:hover .label {
  display: block;
  white-space:nowrap;
}

</style>