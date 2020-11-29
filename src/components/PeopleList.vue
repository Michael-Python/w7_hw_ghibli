<template>
  <div>
      <ul>
          <!-- build thre list from each person in people -->
        <list-item v-for="(person) in people" :person="person" :key="person.id"></list-item>
      </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue'

export default {
    name: 'person-list',
    props: ['people'],
    components:{
        "list-item": ListItem
    }

}
</script>

<style>

</style>