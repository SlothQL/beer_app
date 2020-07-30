<template>
  <div>
      <div>
      <select v-model="beer" v-on:change="handleSelect">
          <option v-for="beer in beers" :beer="beer" :key="beer.id" v-bind:value="beer"> {{ beer.name }} </option>
      </select>
      </div>
      <button v-on:click="addToFavourites" v-bind:class="Object.keys(beer).length > 0 ? 'show' : 'not-show'">Add to Favourites</button>
  </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'beer-select',
    data() {
        return {
            beer: {},
            favouriteBeer: {}
        }
    },
    props: ['beers'],
    methods: {
        handleSelect() {
            eventBus.$emit('selected-beer', this.beer)
        },
        addToFavourites() {
            this.favouriteBeer = this.beer;
            eventBus.$emit('favourite-beer', this.favouriteBeer)
        }
    }
}
</script>

<style scoped>
.show {
   background-color: black ;
   color: white;
   font-weight: bold;
 }

 .not-show {
   display: none;
 }

</style>