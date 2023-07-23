<template>
  <div class="container">
    <mainPage/>
  </div>
</template>

<script>
import mainPage from './components/mainPage.vue'

export default {
  name: 'App',
  components: {
    mainPage
  }
}
</script>

<style lang="scss">
@import './normalize.css';
@import './global.scss'
</style>
