<template>
  <div v-if="beer">
      <h2>{{beer.name}}</h2>
      <h4>Description:</h4>
      <div>{{beer.description}}</div>
        <h4>ABV:</h4>
        <div>{{beer.abv}}</div>
        <h4>Ingredients:</h4>
        <div v-for="(ingredient, key, index) in beer.ingredients">{{ key }}</div>
        <button @click="handleClick()">Add To Favourites!</button>
  </div>
</template>

<script>
import { eventBus } from "../main.js"

export default {
    name: 'beer-detail',
    props: ['beer'],
    methods: {
        handleClick: function(event) { 
            eventBus.$emit("beer-favourite", this.beer)
        }
    }
}
</script>

<style>

</style>