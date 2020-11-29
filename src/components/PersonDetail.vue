<template lang="html">
  <div id="selected_person">
      <!-- information that is important for display on the person level -->
      <div id="display"></div>
        <div id="left-display">
          <h3>{{selectedPerson.name}}</h3>
          <p>{{selectedPerson.gender}}</p>
          <p>species to go here</p>
          <p>Film to go here</p>
        </div>
        <!-- this looks in the static/images folder, within the components folder to pull an image with the same name as the selected person-->
        <div id="right-display">
          <img :src="require(`./static/images/${selectedPerson.name}.jpg`)" width = 50% alt class="icon" />
        </div>
      </div>
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