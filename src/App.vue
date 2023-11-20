<template>
  <div class="wrapper">
    <div v-for="airport in airports" :key="airport.abbreviation">
      <airport-card 
        :airport="airport"
        @addToFavoriteAirports="addToFavoriteAirport($event)"
      />
    </div>
<!-- Favorite Ariports -->
    <h1 v-if="favoriteAirports.length">Favorite Airports</h1>
    <div v-for="airport in favoriteAirports" :key="airport.abbreviation">
      <airport-card :airport="airport" />
   </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import allAirports from '@/data/airports.js'
import AirportCard from '@/components/AirportCard.vue'

export default {
  components: {
    AirportCard
  },
  setup() {
    const airports = ref(allAirports)
    const favoriteAirports = ref([])
    function addToFavoriteAirport($event) {
      var exists = this.favoriteAirports.some(a => {
        return a.id === $event.id;
      });
      if(!exists){
        favoriteAirports.value.push($event);
        console.log(`Add new airport with id ` + $event.id + ` to Fivorite List`);
      }else{
        console.log(`The airport with id ` + $event.id + ` is already in Fivorite List`)
      } 
    }
    return { airports, favoriteAirports, addToFavoriteAirport }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 1rem;
  max-width: 960px;
  margin: 0 auto;
}
</style>
