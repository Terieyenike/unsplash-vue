<template>
  <div>
    <section class="header">
      <div class="search">
        <i class="fas fa-search icon"></i>
        <input
          type="text"
          class="input"
          name="query"
          v-model="query"
          placeholder="Search for photo"
          @keyup.enter="searchPhotos"
        />
      </div>
    </section>
    <image-grid :photos="searchPhoto" />
      <footer class="container">
        <p>Teri Eyenike &copy; 2020</p>
      </footer>
  </div>
</template>

<script>
import axios from "axios";
import ImageGrid from '../ImageGrid'
export default {
  name: "Home",
  components: {
    ImageGrid
  },
  data() {
    return {
      query: "Africa",
      apiKey:
        "cf8e0450c923bf40aa85086880d2e42340a63049558b859327a9a222e499d865",
      apiUrl: "https://api.unsplash.com/search/photos",
      searchPhoto: null
    };
  },
  methods: {
    searchPhotos() {
      const url = `${this.apiUrl}/?query=${this.query}&client_id=${this.apiKey}`;
      // console.log(url);
      axios.get(url).then(response => {
        this.searchPhoto = response.data.results;
      });
      this.query = "";
    }
  },
  created() {
    this.searchPhotos();
  }
};
</script>


<style scoped>
@import "https://use.fontawesome.com/releases/v5.7.2/css/all.css";

.header {
  background: rgb(243, 243, 243);
  padding: 4em 0;
  font-family: Montserrat, sans-serif;
}

input[type="text"] {
  width: 100%;
  padding: 1em;
  border-radius: 0.35em;
  border: 0;
}

.search {
  text-align: center;
  position: relative;
}

.search .input {
  width: 85%;
  text-indent: 30px;
  color: #333;
  font-size: 1rem;
}

.icon {
  position: absolute;
  top: 16px;
  margin-left: 12px;
  color: #d3d2d2;
}
</style>
