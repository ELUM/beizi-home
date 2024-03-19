<script setup>

</script>

<template>
  <div class="left">
    <div class="headSculpture">
      <img src="https://b0.bdstatic.com/092d4259a03e725399027b952e652fd1.jpg@h_1280">
    </div>
    <div class="introduce">
      <div class="tip">私宅榛鹅心</div>
    </div>
  </div>
</template>

<style scoped>

@media (max-width: 1024px) {
  .left {

  }

  .headSculpture {
    width: 100px;
    height: 100px;
  }
}

.left {
  padding: 10px;
}

.headSculpture {
  height: 200px;
  text-align: center;
}

.headSculpture img {
  width: 200px;
  height: 200px;
  border-radius: 50%;
}

.introduce {
  height: 120px;
  border-radius: 10px;
  background: rgba(181, 221, 255, 0.6);
  backdrop-filter: blur(15px);
  padding: 10px;
}

.tip {
  padding: 0 5px;
  width: fit-content;
  white-space: nowrap;
  border-radius: 5px;
  background: rgba(76, 129, 245, 0.95);
  transition: font-size .3s ease;
}

.tip:hover {
  font-size: 32px;
}
</style>