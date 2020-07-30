<template>
  <div v-if="beer">
      <h2>Name: {{ beer.name }}</h2>
      <p>Description: {{ beer.description }}</p>
      <p>Brewers Tips: {{ beer.brewers_tips }}</p>
      <img :src="beer.image_url"/>
  </div>
</template>

<script>
export default {
    name:'beer-detail',
    props: ['beer']
}
</script>

<style>

</style>