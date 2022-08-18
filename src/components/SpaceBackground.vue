<template>
  <div class="spaceBackground"></div>
</template>

<script>
export default {
  name: 'SpaceBackground',
};
</script>
<style lang="scss" scoped>
  .spaceBackground {
    position: fixed;
    top: 0;
    z-index: -1;
    height: 100vh;
    width: 100%;
    background-image: url(../assets/background.jpg);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
  }
  .spaceBackground::after {
    content: '';
    background: rgba(0, 0, 0, .2);
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
    width: 100%;
    height: 100vh;
  }
</style>
