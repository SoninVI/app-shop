<template>
  <div id="app">
    <p>Hello Vue Shop App</p>
    <vMainWrap/>
  </div>
</template>

<script>
import vMainWrap from './components/v-main-wrap'

export default {
  name: 'App',
  components: {
    vMainWrap
  }

}
</script>

<style>
  #app{
    text-align: center;

  }
</style>
