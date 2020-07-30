<template>
  <div>
      <select v-model="beer" v-on:change="handleSelect">
          <option v-for="beer in beers" :beer="beer" :key="beer.id" v-bind:value="beer"> {{ beer.name }} </option>
      </select>
  </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'beer-select',
    data() {
        return {
            beer: {}
        }
    },
    props: ['beers'],
    methods: {
        handleSelect() {
            eventBus.$emit('selected-beer', this.beer)
        }
    }
}
</script>

<style>

</style>