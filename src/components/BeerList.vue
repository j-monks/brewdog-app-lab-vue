<template>
  <div>
      <ul>
        <list-item v-for="(beer, index) in beers" :beer="beer" :key="index"></list-item>
      </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue'

export default {
    name: 'beer-list',
    props: ['beers'],
    components: {
        "list-item": ListItem
    }
}
</script>

<style>

</style>