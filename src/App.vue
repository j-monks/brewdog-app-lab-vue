<template>
  <div>
    <beer-list :beers="beers" />
    <beer-detail :beer="selectedBeer"/>
  </div>
</template>

<script>
import { eventBus } from "./main.js"
import BeerList from './components/BeerList.vue'
import BeerDetail from './components/BeerDetail.vue'
// import FavouriteList from './components/FavouriteList.vue'

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
    },
  mounted() {
      fetch("https://api.punkapi.com/v2/beers")
        .then(result => result.json())
        .then(beerData => {beerData.forEach((beer) => {beer.isFavourite = false});
         this.beers = beerData;})

        eventBus.$on("beer-selected", (beer) => {
          this.selectedBeer = beer;
        })
        // this.beers.forEach(beer => beer['isFavourite'] = false);

    }
  }


</script>


<style>

</style>