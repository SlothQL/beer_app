<template>
  <div>
    <h1>Beers</h1>
    <div>
      <beer-select :beers='beers'></beer-select>
      <beer-detail :beer="selectedBeer"></beer-detail>
    </div>
  </div>
</template>

<script>
import BeerDetail from './components/BeerDetail.vue';
import {eventBus} from '@/main.js';
import BeerSelect from './components/BeerSelect.vue';
export default {
  name: 'app',
  data() {
    return {
      beers: [],
      selectedBeer: null
    };
  },

  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(data => this.beers = data)
    .catch(err => console.log(err))

    eventBus.$on('selected-beer', (beer) => {
      this.selectedBeer = beer;
    })
  },

  components: {
    'beer-select': BeerSelect,
    'beer-detail': BeerDetail
  }
}
</script>

<style>

</style>