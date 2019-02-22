<template>
  <div id="app">
    <AsteroidGrid @remove="remove" :asteroids="asteroids" header="Near-Earth Objects"/>
  </div>
</template>

<script>
import AsteroidGrid from './component/AsteroidGrid.vue'

export default {
  name: 'app',
  components: {
    AsteroidGrid
  }
}
</script>

<style>

</style>
