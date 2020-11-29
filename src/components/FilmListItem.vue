<template>
  <li>{{film.title}}</li>
</template>

<script>
export default {
    // this goes to FilmList
    name: 'film-list-item',
    props: ['film']
}
</script>

<style>

</style>