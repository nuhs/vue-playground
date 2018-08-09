<template>
  <div class="feed">
    <h1>{{ title }}</h1>
    <div class="resp-container">
        <iframe class="resp-iframe" v-bind:src="url"></iframe>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Feed',
  props: ['title', 'url'],
  data () {
    return {}
  }
}
</script>

<style scoped>
.resp-container {
    position: relative;
    overflow: hidden;
    width: 80vw;
    height: 100vh;
    padding-top: 56.25%;
}
.resp-iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: 0;
}
</style>
