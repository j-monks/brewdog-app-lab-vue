<template>
<div>
    <h3>Favourites List:</h3>
    <ul>
        <list-item v-for="(beer, index) in favourites" v-if="beer.isFavourite === true" :beer="beer" :key="index"><button>Unfavourite</button></list-item>
      </ul>
</div>
</template>

<script>
import ListItem from './ListItem.vue'
export default {
    name:'favourites-list',
    props: ['favourites'],
    components: {
        'list-item': ListItem
    }

}
</script>

<style>

</style>