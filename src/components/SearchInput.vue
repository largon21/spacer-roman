<template>
    <div class="wrapperSearch">
      <!-- <label for="search"> Search </label> -->
      <input id="search" name="search" :value="value" :class="{ dark }" @input="handleChange"/>
    </div>
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
    dark: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  .wrapperSearch {
    margin-top: 40px;
    display: flex;
    flex-direction: column;
    width: 300px;

  label {
    front-family: Montserrat, sans-serif;
    margin-top: 30px;
  }

  input {
    text-align: center;
    font-size: 15px;
    font-weight: 200;
    color: rgb(6, 41, 33);
    height: 30px;
    border: 0;
    background: none;
    border-bottom: 1px solid black;
    transition: box-shadow .8s easy-out;
  }

  input:focus {
    outline: none;
    box-shadow: 0 5px 12px -8px rgba(0,0,0, .5);
  }

  .dark {
    color: black;
    border-bottom-color: black;
  }

  .dark:focus {
    box-shadow: 0 10px 20px -8px rgba(255,255,255, .5);
  }
  }

</style>
