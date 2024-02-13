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

<template>
  <div class="ac_container d-flex flex-column  flex-wrap">
    <Aside />
    <Header/> 
    <Main/>
  </div>
</template>

<style lang="scss">
   @use '../scss/main.scss';
</style>
