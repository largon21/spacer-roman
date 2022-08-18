<template>
  <div class="app">
    <div class="nav">
      <router-link to="/">Search</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
* {
  box-sizing: border-box;
}

body {
  font-family: 'Montserrat', sans-serif;
}
</style>
