<template>
  <div v-if="beer">
      <h2>{{beer.name}}</h2>
        <p>Description: {{beer.description}}</p>
        <p>abv: {{beer.abv}}</p>
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