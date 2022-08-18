<template>
  <div class="wrapperHome">
    <SpaceBackground />
    <Claim />
    <SearchInput v-model="searchValue" @input="handleInput" />

  </div>
</template>

<script>
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import SpaceBackground from '@/components/SpaceBackground.vue';

import axios from 'axios';
import _ from 'lodash';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'Home',
  components: {
    Claim,
    SearchInput,
    SpaceBackground,
  },
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: _.debounce(function x() {
      console.log(this.searchValue)
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
<style lang="scss" scoped>
  .wrapperHome {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
    padding: 30px;
    width: 100%;
  }
</style>
