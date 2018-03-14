<template>
  <li class="media-item" v-bind:key="media.trackId">
    <img v-bind:src="media.artworkUrl100">
    <div class="details">
      <h1 class="track">{{ media.trackName }}</h1>
      <span>by</span>
      <h2 class="artist">{{ media.artistName }}</h2>
    </div>
  </li>
</template>

<script>
export default {
  name:'MediaItem',
  props: ['media']
}
</script>

<style scoped>
.track {
  max-height: 55px;
  overflow: hidden;
}

.track, .artist {
  margin: 0;
}

h1 {
  font-size: 1rem;
}

h2 {
  font-size: .9rem;
}

span {
  margin: 7px auto;
}

li.media-item {
  display: inline-block;
  width: 290px;
  height: 105px;
  margin: 10px 5px;
  background-color: #EEE;
  padding: 15px;
  overflow: hidden;
  text-align: left;
}

li.media-item span {
  display: block;
  overflow: hidden;
}

div.details {
  display: inline-block;
  position: absolute;
  width: 180px;
  margin-left: 5px;
}
</style>
