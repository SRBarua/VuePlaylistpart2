<template>
  <div id="app">
        <song-list></song-list>
  </div>
</template>

<script>
    import SongList from './components/SongList.vue'

        export default {
          name: 'app',
              components: {
                    SongList
                }
      }
</script>

<style>
    #app {

    }
</style>
