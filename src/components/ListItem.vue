<template>
  <li v-on:click="handleClick">{{ beer.name }} <button v-if="beer.isFavourite" @click="handleUnfavourite">Unfavourite</button></li>
</template>

<script>
import { eventBus } from "../main.js"
export default {
    name: "list-item",
    props: ["beer"],
    methods: {
        handleClick(){
            eventBus.$emit("beer-selected", this.beer)
        },

        handleUnfavourite(){
            eventBus.$emit("unfavourite", this.beer)
        }
    }
}
</script>

<style>

</style>