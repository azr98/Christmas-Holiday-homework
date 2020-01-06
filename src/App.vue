<template>
  <div id="app">
    <film-drop-down :films="films"></film-drop-down>
    <film-details :film="selectedFilm" />
    <film-list :films="films"/>
    <display-watchlist :watchlist="watchlist"></display-watchlist>
  </div>
</template>

<script>
import FilmList from './components/FilmList'
import {eventBus} from './main.js'
import FilmDetail from './components/FilmDetail'
import FilmDropDown from './components/FilmDropDown'
import DisplayWatchList from './components/DisplayWatchList'

export default {
  name: 'app',
  components: {
    'film-list' : FilmList,
    'film-details' : FilmDetail,
    'film-drop-down': FilmDropDown,
    'display-watchlist' : DisplayWatchList
  },

  data() {
    return{
    films: [],
    watchlist: [],
    selectedFilm: ""
  }
  },

  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film
    })

    eventBus.$on('film-list', (film) => {
      this.addFilmTowatchlist(film)
    })

    
  },

  methods:{
    addFilmTowatchlist(film){
      this.watchlist.push(film)
    }
  }
}
</script>

<style>
#app {


}
</style>
