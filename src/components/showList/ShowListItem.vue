<template>
  <div class="movieListView">
    <img :src="tvShow.image.medium" height="300" />
    <div class="footer">
      <h3>{{ tvShow.name }}</h3>
      <p>Rating: {{ tvShow.rating.average }} / 10</p>
      <p>{{ tvShow.genres.join(", ") }}</p>
    </div>
    <router-link :to="'show?id=' + tvShow.id">
      <div class="footer-link">Read more</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: "ShowListItem",

  props: {
    tvShow: { type: Object },
  },
};
</script>

<style scoped>
.movieListView {
  white-space: normal;
  width: 210px;
  min-height: 550px;
  background-color: white;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  margin-right: 1rem;
  border-radius: 10px;
  position: relative;
  box-shadow: rgba(17, 17, 26, 0.05) 0px 1px 0px,
    rgba(17, 17, 26, 0.1) 0px 0px 8px;
}

.footer {
  padding: 1rem;
}

.footer-link {
  background-color: #1b5299;
  color: white;
  padding: 1rem;
  position: absolute;
  bottom: 0;
  width: 100%;
}

.footer-link a {
  color: white;
  text-decoration: none;
}
</style>
