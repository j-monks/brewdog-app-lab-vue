<template>
  
</template>

<script>
// import BeerList from './components/BeerList.vue'
// import BeerDetail from './components/BeerDetail.vue'
// import FavouriteList from './components/FavouriteList.vue'

export default {
  data() {
    return {
      beers: [],
      selectedBeer: null
    }
  },
  components: {
      // "beer-list": BeerList,
      // "beer-detail": BeerDetail,
    },
  mounted() {
      fetch("https://api.punkapi.com/v2/beers")
        .then(result => result.json())
        .then(beers => this.beers = beers )
    }
  }


</script>


<style>

</style>