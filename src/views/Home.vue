<template>
  <div :class="[{ flexStart: step === 1 }, 'wrapperHome']">
    <transition name="slide">
      <img src="@/assets/logo.svg" class="logo" v-if="step ===1"/>
    </transition>
    <transition name="fade">
      <SpaceBackground v-if="step === 0"/>
    </transition>
    <Claim v-if="step === 0"/>
    <SearchInput v-model="searchValue" @input="handleInput" :dark="step === 1"/>
    <div class="results" v-if="results && !loading && step ===1">
      <Item v-for="item in results" :item="item" :key="item.data[0].nasa_id"/>
    </div>
  </div>

</template>

<script>
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import SpaceBackground from '@/components/SpaceBackground.vue';
import Item from '@/components/Item.vue';

import axios from 'axios';
import _ from 'lodash';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'Home',
  components: {
    Claim,
    SearchInput,
    SpaceBackground,
    Item,
  },
  data() {
    return {
      loading: false,
      step: 0,
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: _.debounce(function x() {
      this.loading = true;
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
          this.loading = false;
          this.step = 1;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>
<style lang="scss" scoped>
  .fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s ease;
  }

  .fade-enter-from, .fade-leave-to {
    opacity: 0;
  }

  .slide-enter-active, .slide-leave-active {
    transition: margin-top 0.5s ease;
  }

  .slide-enter-from, .slide-leave-to {
    margin-top: -50;
  }
  .wrapperHome {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
    padding: 30px;
    width: 100%;
    &.flexStart {
      justify-content: flex-start;
    }
  }

  .logo {
    top: 0px;
  }

</style>
