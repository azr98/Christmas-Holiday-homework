<template lang="html">

  <div class="">
    <h2>Here are all the current films by Ghibli</h2>
    <label for="film_select">Select a film for more details</label>
    <select id="film_select" @change="handleChange" v-model="selectedFilm">
      <option disabled value="">Select a film</option>
      <option v-for="(film,index) in films" :key='index' :value="film">{{film.title}}</option>
    </select>
  </div>

</template>

<script>
import {eventBus} from '../main.js'


export default {
  name: 'film-drop-down',
  props: ['films'],

  data(){
    return {
      selectedFilm: null
    }
  },

  methods: {
    handleChange(event){
      eventBus.$emit('film-selected',this.selectedFilm)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
