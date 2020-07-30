<template>
  <div>
      <h2>{{beer.name}}</h2>
        <p>Description: </p>
        <p>abv: </p>
  </div>
</template>

<script>
export default {
    name: 'beer-detail',
    props: ['beer']
}
</script>

<style>

</style>