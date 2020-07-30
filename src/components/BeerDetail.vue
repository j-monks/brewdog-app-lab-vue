<template>
  <div>
      <h2>{{beer.name}}</h2>
        <p>Description: {{beer.description}}</p>
        <p>abv: {{beer.abv}}</p>
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