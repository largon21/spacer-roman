<template>
  <div :style="style" class="item"></div>
</template>

<script>
export default {
  name: 'Item',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      photo: this.item.links[0].href,
      title: this.item.links[0].title,
    };
  },
  computed: {
    style() {
      return `backgroundImage: url("${this.photo}")`;
    },
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.item {
  width: 300px;
  height: 300px;
  background-size: cover;
  background-repeat: no-repeat;
}
</style>
