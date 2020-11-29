<template lang="html">
  <div id="selected_person">

    <!-- information that is important for display on the person level -->
    <div id="display"></div>

      <div id="left-display">
        <h3>{{selectedPerson.name}}</h3>
        <p>{{selectedPerson.gender}}</p>
      </div>
      
      <!-- this looks in the static/images folder, within the components folder to pull an image with the same name as the selected person-->
      <div id="right-display">
        <img :src="require(`./static/images/${selectedPerson.name}.jpg`)" alt class="profile" />
      </div>

      <div id="films">
        <!-- the main problem is here, I think: I should not be referring to selectedPerson for the value for the films array; however, deleting 'selectedPerson.' before 'films' takes away any input from film list-->
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
  components: {
    'film-list': FilmList
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
      .then(response => response.json())
      // .then(data => console.log(data))
      // this makes the data from the of people line above = to the array 
      .then(data => this.films = data)
  },
  watch: {
    selectedPerson: function() {
      this.getFilms;
    }
  },
//   methods: {
//     getFilms() {
//       // the map function gets an array of films for each person, these are 'promised' to happen
//       const filmsPromises = this.people.films.map((films) => {
//         // this takes the fetch information and converts it to json format
//         return fetch(films).then(res => res.json());
//       })
//       // the promise.all function ensures all individual promises are resolved
//       Promise.all(filmsPromises)
//       .then((data) => {
//         this.films = data; 
//       })
    // }
  // }
  
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