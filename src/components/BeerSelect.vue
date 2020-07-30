<template>
  <div>
      <select v-model="beer" v-on:change="handleSelect">
          <option v-for="beer in beers" :beer="beer" :key="beer.id" v-bind:value="beer"> {{ beer.name }} </option>
      </select>
  </div>
</template>

<script>
export default {
    name: 'beer-select',
    data() {
        return {
            beer: {}
        }
    },
    props: ['beers']
}
</script>

<style>

</style>