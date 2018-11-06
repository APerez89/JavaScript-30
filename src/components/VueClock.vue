<template>
  <div class="clock-container">
    <div class="clock">
      <div class="clock-face">
        <div class="hand hour-hand"></div>
        <div class="hand min-hand"></div>
        <div class="hand sec-hand"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
};
</script>

<style lang="scss" scoped>
.clock-container {
  width: 100vw;
  height: 100vh;
  background: #018DED url('http://unsplash.it/1500/1000?image=881&blur=50');
  background-size: cover;
  background-repeat: no-repeat;
  display: flex;
  justify-content: center;
  align-items: center;
  .clock {
    width: 250px;
    height: 250px;
    border: 10px solid #fff;
    border-radius: 50%;
    position: relative;
    padding: 10px;
    .clock-face {
      width: 100%;
      height: 100%;
      position: relative;
      .hand {
        width: 50%;
        border: 3px solid #fff;
        position: absolute;
        top: 50%;
        transform-origin: 100%;
        transform: rotate(90deg);
        transition: all 0.5s;
        transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1);
      }
      .hour-hand {
        left: 25%;
        width: 25%;
        border-color: #101010;
        transform: rotate(100deg);
      }
      .min-hand {
        width: 40%;
        left: 10%;
        border-color: #523e3e;
        transform: rotate(150deg);
      }
      .sec-hand {
        border-color: #706a6a;
        transform: rotate(130deg);
      }
    }
  }
}
</style>
