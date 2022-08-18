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
    margin: 0;
    padding: 30px;
    width: 100%;
  }


</style>
