<template>
  <div class="wrapper">
    <Claim />
    <SearchInput />

  </div>
</template>

<script>
import Claim from '@/components/Claim';
import SearchInput from '@/components/SearchInput';

export default {
  name: 'Search',
  components: {
    Claim,
    SearchInput,
  },
};
</script>
<style lang="scss" scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
    padding: 30px;
    width: 100%;
    background-image: url(../assets/background.jpg);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
  }


</style>
