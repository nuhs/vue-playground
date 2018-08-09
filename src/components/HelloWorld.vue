<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="container">
      <nav>
        <ul>
          <li
            v-for="track in tracks"
            v-bind:key="track.itemid"
            v-on:click="selectedTrack(track)">
            <img
              border="1"
              v-bind:src="track.thumb_url_medium"/>
            {{ track.title }}
          </li>
        </ul>
      </nav>
      <article>
        <feed
          v-bind:title="selected.title"
          v-bind:url="selected.posturl"></feed>
      </article>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'

let axios = require('axios')
let Feed = require('@/components/Feed').default

export default {
  name: 'HelloWorld',
  data () {
    return {
      selected: { title: '', url: '' },
      tracks: null,
      msg: 'Welcome to hypem!'
    }
  },
  mounted () {
    axios
      .get('https://api.hypem.com/v2/tracks?sort=popular')
      .then(response => (this.tracks = response.data))
  },
  methods: {
    selectedTrack: function (track) {
      console.log(track)
      this.selected = track
    }
  }
}

Vue.component('feed', Feed)
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.container {
  display: flex;
}
</style>
