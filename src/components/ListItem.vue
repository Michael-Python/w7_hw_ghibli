<template>
   <li v-on:click="handleClick">{{person.name}}</li>
</template>

<script>
export default {
    name: 'list-item',
    props: ['person'],
    methods: {
        handleClick(){
            eventBus.$emit('person-selected', this.person)
        }
    }

}
</script>

<style>

</style>