<template>
  <div class="airport" @click="$emit('addToFavoriteAirports', airport)">
    <p>{{ airport.abbreviation }}</p>
    <p>{{ airport.name }}</p>
    <p>{{ airport.city }}, {{ airport.state }}</p>
  </div>
</template>

<script>
export default {
  props: {
    airport: {
      type: Object,
      required: true
    }
  },
  setup() {
    function selectAirport(airport) {
      alert(`You clicked on ${airport.abbreviation}. It's located in ${airport.city}, ${airport.state}.`)
    }
    return { selectAirport }
  }
}
</script>

<style scoped>
.airport {
  border: 3px solid;
  border-radius: .5rem;
  padding: 1rem;
}

.airport p:first-child {
  font-weight: bold;
  font-size: 2.5rem;
  margin: 1rem 0;
}

.airport p:last-child {
  font-style: italic;
  font-size: .8rem;
}
</style>