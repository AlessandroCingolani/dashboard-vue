<template>

  <Aside />
  <Header/> 
  <Main/>
</template>

<script>
import Aside from './components/Aside.vue'
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Aside,
    Header,
    Main
  }
}
</script>

<style lang="scss">
   @use '../scss/main.scss';
</style>
