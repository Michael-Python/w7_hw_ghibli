<template>
  <div class="body">
    <header class="header">Studio Ghibli API</header>
    <div class="main-container"></div>
      <people-list :people="people"></people-list>
      <person-detail :person="selectedPerson" v-if="selectedPerson"></person-detail>

  </div>
</template>

<script>
import PeopleList from './components/PeopleList.vue'
import PersonDetail from './components/PersonDetail.vue'
export default {
  name: 'app',
  data() {
    return {
      ghiblis: [],
      selectedGhibli: null,
    };
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/people/')
    .then(res => res.json())
    .then(people => this.people = people)

  
    },
    components: {
      "people-list": PeopleList,
      "person-detail": PersonDetail
    }
}



</script>

<style>

</style>