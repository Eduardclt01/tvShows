<script setup>
import ShowFilters from "../components/filters/ShowFilters.vue";
import ShowList from "../components/showList/ShowList.vue";
</script>

<template>
  <main>
    <ShowFilters
      :onSearchBySting="onSearchBySting"
      :getFilteredData="getFilteredData"
      :setRating="setRating"
      :setGenre="setGenre"
    />
    <ShowList :tvShows="this.shows" />
  </main>
</template>

<script>
export default {
  name: "MainView",

  data() {
    return {
      shows: [],
      allShows: [],
      searchedShows: [],
      searchActive: false,
      search: "",
      genre: "",
      rating: "",
    };
  },

  methods: {
    setGenre(genre) {
      this.genre = genre;
    },

    setRating(rating) {
      this.rating = rating;
    },

    getFilteredData() {
      let filterShows = this.searchActive ? this.searchedShows : this.allShows;

      if (this.rating === "" && this.genre === "") {
        this.shows = filterShows;
        return;
      }

      this.shows = filterShows.filter((show) => {
        // Filter by rating and genre
        if (this.rating !== "" && this.genre !== "") {
          return (
            show.rating.average >= this.rating &&
            show.genres.includes(this.genre)
          );
        } // Filter by rating only
        else if (this.rating !== "" && this.genre === "") {
          return show.rating.average >= this.rating;
        } // Filter by genre only
        else if (this.rating === "" && this.genre !== "")
          return show.genres.includes(this.genre);
      });
    },

    onSearchBySting(event) {
      let searchString = event.target.value;

      if (searchString === "") {
        this.searchActive = false;
        return;
      } else {
        this.searchActive = true;
        this.searchedShows = this.allShows.filter((show) =>
          show.name.toLowerCase().includes(searchString)
        );
        this.shows = this.searchedShows;
      }
    },

    getAllTvShows() {
      fetch(`https://api.tvmaze.com/shows`)
        .then((response) => response.json())
        .then((res) => {
          this.allShows = res;
          this.shows = this.allShows;
        });
    },
  },
  created() {
    this.getAllTvShows();
  },
};
</script>
