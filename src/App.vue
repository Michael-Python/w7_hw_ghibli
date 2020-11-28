<template>
  <div id ="app">
    <h1>Studio Ghibli</h1>    
    <!-- <div class="main-container">
      <!-- <people-list :people='people'></people-list> -->
      
    <!-- </div> --> 
    <!-- sets up a select box to pull items from the people array -->
    <label for="person_select">Click to select a person from a film: </label>
    <select id="person_select" v-model="selectedPerson">
      <option disabled value=""></option>
      <option v-for="(person, index) in people" :key="index" :value="person">{{person.name}}</option>

    </select>
    <!-- this defines person as the selected person from the select part of the web page -->
    <person-detail :person='selectedPerson' v-if='selectedPerson'></person-detail>
  </div>

</template>

<script>
import PersonDetail from './components/PersonDetail.vue'
// import PeopleList from './components/PeopleList.vue'
import { eventBus } from './main.js'

export default {
  name: 'app',
  data(){
    return{
      people: [],
      selectedPerson: null
    };
  },
  components:{
    'person-detail': PersonDetail,
    // 'people-list': PeopleList,

  },
  methods(){

  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/people')
    .then(response => response.json())
    // .then(data => console.log(data))
    // this makes the data from the of people line above = to the array 
    .then(data => this.people = data)

    eventBus.$on("person-selected", (person) => {
      this.selectedPerson = person;
    })
  }
}
</script>

<style>

</style>