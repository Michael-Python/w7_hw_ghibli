<template lang="html">
  <div>
      <!-- information that is important for display on the person level -->
      
      Hi there
      <h3>{{selectedPerson.name}}</h3>
      <p>{{selectedPerson.gender}}</p>
      <p>species to go here</p>
      <p>Film to go here</p>
      <!-- <p><img src="{}.jpg".format(selectedPerson.name)></p> -->
  </div>
</template>

<script>
export default {
  name: 'person-detail',
  props: ['selectedPerson'],
  
}
</script>

<style>

</style>