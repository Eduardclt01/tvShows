<template>
  <div class="movieContainer">
    <div class="row">
      <div class="col-md-12">
        <div class="filterInput">
          <input
            type="text"
            v-model.trim="search"
            placeholder="Search..."
            @keyup="onSearchBySting"
          />
        </div>

        <p>Filter</p>
        <div class="filterInput">
          <select @change="setGenre($event.target.value)" placeholder="Genre">
            <option></option>
            <option>Action</option>
            <option>Adult</option>
            <option>Adventure</option>
            <option>Anime</option>
            <option>Children</option>
            <option>Comedy</option>
            <option>Crime</option>
            <option>DIY</option>
            <option>Drama</option>
            <option>Espionage</option>
            <option>Family</option>
            <option>Fantasy</option>
            <option>Food</option>
            <option>History</option>
            <option>Horror</option>
            <option>Legal</option>
            <option>Medical</option>
            <option>Music</option>
            <option>Mystery</option>
            <option>Nature</option>
            <option>Romance</option>
            <option>Science-Fiction</option>
            <option>Sports</option>
            <option>Supernatural</option>
            <option>Thriller</option>
            <option>Travel</option>
            <option>War</option>
            <option>Western</option>
          </select>
        </div>

        <div class="filterInput">
          <input
            type="text"
            placeholder="Rating"
            @keyup="setRating($event.target.value)"
          />
        </div>

        <div class="row">
          <button @click="getFilteredData">Filter</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ShowFilters",

  props: {
    onSearchBySting: { type: Function },
    getFilteredData: { type: Function },
    setRating: { type: Function },
    setGenre: { type: Function },
  },
};
</script>

<style scoped>
.movieContainer {
  padding: 1rem;
}

.filterInput {
  margin-bottom: 1rem;
}
</style>
