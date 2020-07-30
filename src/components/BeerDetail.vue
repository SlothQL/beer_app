<template>
  <div v-if="beer" class="wrapper">
        <img class="img" :src="beer.image_url"/>
        <div class="beer-details">
        <h2>Name: {{ beer.name }}</h2>
        <p>Description: {{ beer.description }}</p>
        <p>Brewers Tips: {{ beer.brewers_tips }}</p>
        </div>
  </div>
</template>

<script>
export default {
    name:'beer-detail',
    props: ['beer']
}
</script>

<style scoped>
 .img {
     height: 200px;
 }

.wrapper {
    display: flex;
    align-items: center;
}
.beer-details {
    margin-left: 30px;
}
</style>