<template lang="html">
  <div id="selected_person">
      <!-- information that is important for display on the person level -->
      
      <h3>{{selectedPerson.name}}</h3>
      <p>{{selectedPerson.gender}}</p>
      <p>species to go here</p>
      <p>Film to go here</p>
      <!-- this looks in the static/images folder, within the components folder to pull an image with the same name as the selected person-->
      <img :src="require(`./static/images/${selectedPerson.name}.jpg`)" width = 50% alt class="icon" />
  </div>
</template>

<script>
export default {
  name: 'person-detail',
  props: ['selectedPerson'],
  // data() {
    // return {
    //   films: []
    // }
  // }
//   mounted() {
//     this.getFilms();
//   },
//   methods: {
//     getFilms() {
//       // the map function gets an array of films for each person, these are 'promised' to happen
//       const filmPromises = this.person.film.map((film) => {
//         // this takes the fetch information and converts it to json format
//         return fetch(film).then(resource => resource.json());
//       })
//       console.log(filmPromises);
//     }
  // }
  
}
</script>

<style>

</style>