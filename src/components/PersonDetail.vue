<template>
  <div v-if="person" id="personDetail">
      <div id="film-list-wrapper">
          <film-list v-if="film.length" :films="films"></film-list>
      </div>
  </div>

</template>

<script>
import FilmList from './components/FilmList.vue'
export default {
    name: 'person-detail',
    props: ['person'],
    data() {
        return {
            films: []
        }
    },
    components: {
        'film-list': FilmList
    },
    mounted() {
        this.getFilms();
    },
    methods: {
        getFilms() {
            const filmPromises = this.person.film.map((film) => {
                return fetch(film).then(res => res.json());
            })
            Promise.all(filmPromises)
            .then((data) => {
                this.episodes = data;
                console.log(data);
            })
            console.log(filmPromises);
        }
    }
}
</script>

<style>

</style>