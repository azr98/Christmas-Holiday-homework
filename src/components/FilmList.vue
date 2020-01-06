<template lang="html">
  <div class="">

    <ul >

    <li v-for="(film,index) in films" :key="index">
      <button :value="film" @click="handleClick(film)">
      Add film to watch list</button>
      {{film.title}}
    </li>
    
    </ul>

  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'film-list',
  props: ['films'],

  methods: {
    handleClick(film){
      eventBus.$emit('film-list',film)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
