<script setup>

</script>

<template>
  <div class="left">
    <div class="box">
        <div class="headSculpture">
          
        </div>
        <div class="introduce">
            <div class="tip">私宅榛鹅心</div>
        </div>
    </div>
  </div>
</template>

<style scoped>

@media (min-width: 1024px) {
  .left {

  }
}
.left{
  position: relative;
}
.box{
  width: 246px;
  padding:  15px;
  display: block;
  flex-direction: column;
}
.headSculpture{
  display: block;
  position: absolute;
  top: 0;
  left: 10%;
  width: 190px;
  height: 190px;
  margin:0 auto ;
  background-image: url('https://b0.bdstatic.com/092d4259a03e725399027b952e652fd1.jpg@h_1280');
  background-color: aliceblue;
  border-radius: 50%;
}
.introduce{
  display: block;
  position: absolute;
  top: 210px;
  left: 7%;
  width: 200px;
  height: 120px;
  border-radius: 25px;
  background: rgba(181, 221, 255, 0.6);
  backdrop-filter:blur(15px)
}
.tip{
  display: inline-block;
  margin: 10px;
  padding: 0 5px;
  height: 24px;
  widows: fit-content;
  white-space: nowrap;
  border-radius: 5px;
  background: rgba(76, 129, 245, 0.95);
  font-family: '';
}
@keyframes am1{
  0%{}
}
</style>