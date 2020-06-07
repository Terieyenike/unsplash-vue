<template>
  <div class="unsplash">
    <Home />
  </div>
</template>

<script>
import Home from "./components/layout/Home";
export default {
  components: {
    Home
  }
};
</script>

<style lang="css">
@import url("https://fonts.googleapis.com/css?family=Fira+Sans|Montserrat&display=swap");
.container {
  margin: 0 auto;
  max-width: 1000px;
  width: 75%;
}

footer {
  text-align: center;
  padding: 1.5em 0 0;
}

footer p {
  font-family: "Fira Sans";
  position: sticky;
}
</style>>