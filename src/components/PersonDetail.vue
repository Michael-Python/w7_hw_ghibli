<template>
  <div>
      <!-- information that is important for display on the person level -->
      <h3>{{person.name}}</h3>
      <p>{{person.gender}}</p>
      <p>Film to go here</p>
  </div>
</template>

<script>
export default {
    name: 'person-detail',
    props: ['selectedPerson']
}
</script>

<style>

</style>