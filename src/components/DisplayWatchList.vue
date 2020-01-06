<template lang="html">
  <div class="">

  <h3>Here are the moveis in your watchlist</h3>

  <ul>
    <li v-for="(film,index) in watchlist" :key="index">{{film.title}}
  </ul>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'display-watchlist',
  props: ['watchlist'],

  methods: {
    handleDeleteButton(film){
      eventBus.$emit('delete-film-watchlist',film)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
