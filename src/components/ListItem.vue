<template>
  <!-- populate ul from people object with each person's name -->
  <li v-on:click="handleClick">{{person.name}}</li>
</template>


<script>
// just the eventBus gets imported
import { eventBus } from '../main.js'

export default {
    name: 'list-item',
    // this comes from PersonDetail
    props: ['person'],
    methods: {
        handleClick(){
            // lets me see the output in the console
            // console.log('person', this.person);
            // emit the information back to app.vue, 'channel to broadcast on' and 'what you are broadcasting'
            eventBus.$emit('person-selected', this.person)
        } 
    }

}
</script>

<style>

</style>