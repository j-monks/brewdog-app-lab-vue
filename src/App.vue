<template>
  <div>
    <beer-list :beers="beers" />
    <beer-detail :beer="selectedBeer"/>
    <favourites-list :favourites="beers" />
  </div>
</template>

<script>
import { eventBus } from "./main.js"
import BeerList from './components/BeerList.vue'
import BeerDetail from './components/BeerDetail.vue'
import FavouritesList from './components/FavouritesList.vue'

export default {
  data() {
    return {
      beers: [],
      selectedBeer: null
    }
  },
  components: {
      "beer-list": BeerList,
      "beer-detail": BeerDetail,
      "favourites-list": FavouritesList
    },
  mounted() {
    
    Promise.all([
      fetch("https://api.punkapi.com/v2/beers?page=1&per_page=80")
        .then(result => result.json())
        .then(beerData => {beerData.forEach((beer) => {beer.isFavourite = false});
         this.beers = beerData;}),
      fetch("https://api.punkapi.com/v2/beers?page=2&per_page=80")
        .then(result => result.json())
        .then(beerData => {beerData.forEach((beer) => {beer.isFavourite = false});
         this.beers = this.beers.concat(beerData);})
    ])
    

        eventBus.$on("beer-selected", (beer) => {
          this.selectedBeer = beer;
        })

        eventBus.$on("beer-favourite", (beer) => {
          const index = this.beers.indexOf(beer);
          this.beers[index].isFavourite = true;
        })

        eventBus.$on("unfavourite", (beer) => {
          const index = this.beers.indexOf(beer);
          this.beers[index].isFavourite = false;
        })

    }
  }


</script>


<style>

</style>