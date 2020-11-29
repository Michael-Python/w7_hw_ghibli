<template>
  <div>
      <h3>Film List</h3>
      <ul>
          <film-list-item v-for="(film, index) in films" :key="index" :film="film"></film-list-item>
      </ul>
  </div>
</template>

<script>
// This allows film to display in the unordered list
import FilmListItem from './FilmListItem.vue'

export default {
    // this goes to PersonDetail
    name: 'film-list',
    props: ['films'],
    components:{
        "film-list-item": FilmListItem
    }


}
</script>

<style>

</style>