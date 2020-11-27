<template>
  <div>
      <ul>
          <list-item v-for="(person , index) in people" :person="person" :key="index"></list-item>
      </ul>
  </div>
</template>

import ListItem from './ListItem.vue';
<script>
export default {
    name: 'people-list',
    props: ['people'],
    components: {
        'list-item': ListItem
    }
}
</script>

<style>

</style>