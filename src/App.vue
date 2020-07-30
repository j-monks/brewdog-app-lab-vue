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
      fetch("https://api.punkapi.com/v2/beers")
        .then(result => result.json())
        .then(beerData => {beerData.forEach((beer) => {beer.isFavourite = false});
         this.beers = beerData;})

        eventBus.$on("beer-selected", (beer) => {
          this.selectedBeer = beer;
        })

        eventBus.$on("beer-favourite", (beer) => {
          const index = this.beers.indexOf(beer);
          this.beers[index].isFavourite = true;
        })

    }
  }


</script>


<style>

</style>