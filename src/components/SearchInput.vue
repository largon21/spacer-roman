<template>
    <div class="search">
      <label for="search"> Search </label>
      <input id="search" name="search" v-model="searchValue" @input="handleInput"/>
    </div>
</template>

<script>
import axios from 'axios';
import _ from 'lodash';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'SearchInput',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: _.debounce(function x() {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  .search {
    display: flex;
    flex-direction: column;
    width: 300px;

    label {
      front-family: Montserrat, sans-serif;
      margin-top: 30px;
    }

    input {
      height: 30px;
      border: 0;
      border-bottom: 1px solid black;
    }
  }

</style>
