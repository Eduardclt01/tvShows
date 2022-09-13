<template>
  <ul class="movieList">
    <li v-for="show in tvShows" :key="show.id" class="movieListItem">
      <ShowListItem :tvShow="show" />
    </li>
  </ul>
</template>

<script>
import ShowListItem from "./ShowListItem.vue";
export default {
  name: "ShowList",
  props: {
    tvShows: { type: Array },
  },
  data() {
    return {};
  },
  mounted() {},
  methods: {},
  created() {},
  components: { ShowListItem },
};
</script>

<style scoped>
.movieList {
  overflow: auto;
  white-space: nowrap;
  /* background-color: rgb(232, 232, 232); */
  padding: 1rem;
}

.movieListItem {
  display: inline-block;
}
</style>
