<template lang="html">
  <div id="selected_person">
      <!-- information that is important for display on the person level -->
      <div id="display"></div>
        <div id="left-display">
          <h3>{{selectedPerson.name}}</h3>
          <p>{{selectedPerson.gender}}</p>
          <p>species to go here</p>
          
        </div>
        <!-- this looks in the static/images folder, within the components folder to pull an image with the same name as the selected person-->
        <div id="right-display">
          <img :src="require(`./static/images/${selectedPerson.name}.jpg`)" width = 50% alt class="icon" />
        </div>
        <div id="film">
          <p><film-list v-if="films.length" :films="films"></film-list></p>
        </div>
      </div>
  </div>
</template>

<script>
// This gets information from the film list file
import FilmList from './FilmList.vue';

export default {
  name: 'person-detail',
  props: ['selectedPerson'],
  // this makes PersonDetail a parent of FilmDetail
  data() {
    return {
      // films is the array!!
      films: []
    }
  },
  componenents: {
    'film-list': FilmList
  },
  mounted() {
    this.getFilms();
  },
  watch: {
    selectedPerson: function() {
      this.getFilms;
    }
  },
  methods: {
    getFilms() {
      // the map function gets an array of films for each person, these are 'promised' to happen
      const filmsPromises = this.person.films.map((film) => {
        // this takes the fetch information and converts it to json format
        return fetch(films).then(resource => resource.json());
      })
      // the promise.all function ensures all individual promises are resolved
      Promise.all(filmsPromises)
      .then((data) => {
        this.films = data; 
      })
    }
  }
  
}
</script>

<style>
#selected_person {
  box-sizing: border-box;
  height: 100%;
  width: 80%;
  background: #eee;
  color: #222;
  padding: 10px;
  border: 1px solid #ccc;
  display: flex;
}
#display {
  display: flex;
  justify-content: space-between;
}
#left-display, #right-display {
  width: 45%;
}

#right-display img {
  width: 100%;
}

</style>