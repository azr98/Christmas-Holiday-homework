<template lang="html">
  <div class="">
    <h3>Here are the details of the {{film.title}}</h3>
    <p>Description: {{film.description}}</p>
    <p>Director: {{film.director}}</p>
    <p>Release Date: {{film.release_date}}</p>
    <p>Rotton Tomato score: {{film.rt_score}}</p>
  </div>


</template>

<script>
export default {
  name: 'film-details',
  props: ['film']
}
</script>

<style lang="css" scoped>
</style>
