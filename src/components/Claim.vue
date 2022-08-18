<template>
  <div class="claimWrapper ">
    <h1 class="claim">SPACER</h1>
    <p class="subclaim">
      Begin your jouney through our amazing galaxy,
      and discover places you never even heard of.
    </p>
    <p class="subclaim">
      Type anything space-related to start.
    </p>
  </div>
</template>

<script>
export default {

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  .claimWrapper {
    display: flex;
    text-align: center;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .claim {
    font-size: 50px;
    margin: 0;
  }

  .subclaim {
    font-size: 14px;
    margin: 20px 0 0 0 0;
  }

</style>
