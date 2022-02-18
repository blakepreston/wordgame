<template>
  <HelloWorld/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  beforeCreate(){
        document.querySelector('body').setAttribute('style', 'background:#0d0221')
  }
}
</script>

<style>
@import url(https://fonts.googleapis.com/css?family=Oswald);

#app {
  font-family: Oswald, sans-serif;
  background-color: #0d0221;
  text-align: center;
}
</style>
