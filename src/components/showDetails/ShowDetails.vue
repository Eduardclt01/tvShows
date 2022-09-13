<template>
  <div v-if="showDetails" class="container">
    <img
      class="showImage"
      v-if="showDetails.image"
      :src="showDetails.image.original"
      height="300"
    />
    <h1>{{ showDetails.name }}</h1>
    <p>{{ showDetails.premiered }}</p>

    <p v-if="showDetails.rating">{{ showDetails.rating.average }} / 10</p>
    <p v-html="showDetails.summary"></p>
    <router-link :to="'/'">
      <div class="footer-link">Back to home</div>
    </router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showId: "",
      showDetails: {},
    };
  },
  methods: {
    getTvShowById() {
      fetch(`https://api.tvmaze.com/shows/${this.showId}`)
        .then((response) => response.json())
        .then((res) => {
          this.showDetails = res;
        });
    },
  },
  created() {
    let urlParams = new URLSearchParams(window.location.search);
    this.showId = urlParams.get("id");

    this.getTvShowById();
  },
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  max-width: 40rem;
  margin: auto;
}

.showImage {
  align-self: start;
}
</style>
