<template>
  <div>
    <h1>Beers</h1>
    <div>
      <beer-select :beers='beers'></beer-select>
      <beer-detail :beer="selectedBeer"></beer-detail>
      <list-favourite-beers :favouriteBeers="favouriteBeers"></list-favourite-beers>
    </div>
  </div>
</template>

<script>
import ListFavouriteBeers from './components/ListFavouriteBeers.vue';
import BeerDetail from './components/BeerDetail.vue';
import {eventBus} from '@/main.js';
import BeerSelect from './components/BeerSelect.vue';
export default {
  name: 'app',
  data() {
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };
  },

  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(data => this.beers = data)
    .catch(err => console.log(err))

    eventBus.$on('selected-beer', (beer) => {
      this.selectedBeer = beer;
    }),
    eventBus.$on('favourite-beer', (beer) => {
      this.favouriteBeers.push(beer);
    })
  },

  components: {
    'beer-select': BeerSelect,
    'beer-detail': BeerDetail,
    'list-favourite-beers': ListFavouriteBeers
  }
}
</script>

<style>
 
</style>