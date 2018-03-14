<template>
  <div id="app">
    <div class="search-intro">
      <form @submit="search">
          <label for="search-term">Search for a Song</label>
          <fieldset>
            <input id="search-term" name="search-term" value="">
            <input type="submit" value="Search">
          </fieldset>
      </form>
    </div>
    <ul>
      <MediaItem
        v-for="item in results"
        v-bind:media="item"
      ></MediaItem>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
import MediaItem from './components/MediaItem.vue'

export default {
  name: 'app',
  components: { MediaItem },
  data: function () {
    return {
      results: []
    }
  },
  methods: {
    search: function (e) {
      e.preventDefault()

      axios.get('https://itunes.apple.com/search?media=music&entity=song&term=' + document.getElementsByName('search-term')[0].value)
        .then((response) => {
          console.log(response)
          this.results = response.data.results
        }).catch(console.error.bind(console, 'Fetch error:'))
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 100%;
  text-align: center;
  margin: 0 auto;
}

body {
  margin: 0;
  padding: 0;
  background-color: #333;
}

ul {
  margin: 210px 0 0 0;
  padding: 0;
}

fieldset {
  border: none;
  text-align: center;
}

label, input {
  display: block;
  margin: 5px auto 0;
}

label {
  text-align: center;
}

input {
  display: inline-block;
  border: none;
  padding: 10px 10px;
  width: 400px;
  font-size: 16px;
}

input[type=submit] {
  width: 140px;
  background-color: #333;
  color: #DDD;
  padding: 10px 10px;
  text-align: center;
  text-decoration: none;
}

input[type=submit]:hover {
  cursor: pointer;
}

img {
  display: inline-block;
}

form {
  margin-top: 30px;
}

label[for=search-term]{
  color: #DDD;
  font-size: 2.5rem;
  font-family: fantasy;
}

.search-intro {
  position: fixed;
  width: 100%;
  height: 200px;
  top: 0;
  left: 0;
  z-index: 999;
  background: url(./assets/musics.jpg) bottom center no-repeat;
}
</style>
