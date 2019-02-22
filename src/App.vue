<template>
  <div id="app">
    <AsteroidGrid @remove="remove" :asteroids="asteroids" header="Near-Earth Objects"/>
  </div>
</template>

<script>
import AsteroidGrid from './components/AsteroidGrid.vue'

export default {
  name: 'app',
  components: {
    AsteroidGrid
  },
  data() {
    return {
      asteroids: []
    }
  },            
  created: function () {
    this.fetchAsteroids();
  },
  methods: {
    fetchAsteroids:
      function () {
        var apiKey = 'qtbDAzGCDR7zrNAypKP7VrE3zxUyL76W9nFsp1at';
        var url = `https://api.nasa.gov/neo/rest/v1/neo/browse?api_key=${apiKey}`;
        fetch(url)
        .then((res) => res.json())
        .then((val) => {
          this.asteroids = val.near_earth_objects.slice(10, 20);
          });
        },
      remove: 
        function (index) {
          this.asteroids.splice(index, 1);
        }
    }
}
</script>

<style>
  [v-cloak] {
    display: none;
  }
</style>
