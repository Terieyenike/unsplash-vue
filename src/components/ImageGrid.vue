<template>
  <div>
    <section class="random">
      <div class="container card">
        <div class="card-box" v-for="photo in photos" :key="photo.id">
          <div class="overlay"></div>
          <img :src="photo.urls.regular" :alt="photo.alt_description" class="img" />

          <div class="card-info">
            <p>{{photo.user.name}}</p>
            <p>{{photo.user.location}}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "image-grid",
  props: {
    photos: Array
  }
};
</script>


<style>
.img {
  height: 100%;
  object-fit: cover;
  width: 100%;
}

.random {
  margin-top: -2em;
 
}
.card {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-flow: dense;
  gap: 1.5rem;
  cursor: pointer;
}

.card-box {
  position: relative;
  /* border-radius: 0.75em; */
  overflow: hidden;
}

.card-info {
  position: absolute;
  /* top: 0; */
  bottom: 0;
  /* left: 0;
  right: 0; */
  display: grid;
  align-content: end;
  padding: 1.3em;
  /* z-index: 0; */
  color: white;
  transition: all 1s ease;
}

.overlay {
  background: linear-gradient(to top, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.1));
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  z-index: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  /* border-radius: 5em; */
}

.card-info--detail {
  display: flex;
}

@media only screen and (max-width: 1000px) {
  .card {
    grid-template-columns: 1fr;
  }
}
</style>

