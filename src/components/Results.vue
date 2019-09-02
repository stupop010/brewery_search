<template>
  <div class="container">
    <div class="flex">
      <div class="card" v-for="brew in this.brew" :key="brew.id">
        <h1>{{brew.name}}</h1>
        <p>{{brew.city}}</p>
        <p>{{brew.state}}</p>
        <p>{{brew.country}}</p>
        <a :href="brew.website_url" target="_blank">Website</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Results",
  props: {
    brew: Array
  }
};
</script>

<style scoped>
.container {
  width: 80%;
  margin: 2em auto;
}

.flex {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.card {
  width: 23%;
  border: 1px solid rgba(11, 11, 11, 0.7);
  border-radius: 5px;
  box-shadow: 1px 1px rgba(48, 48, 47, 0.6);
  margin: 0.5em 0;
  padding-bottom: 1em;
  background: linear-gradient(
    rgba(11, 11, 11, 0.5) 10%,
    30%,
    rgba(237, 240, 238, 0.5) 90%
  );
}
.card > h1 {
  font-size: 1.3em;
  font-weight: 600;
  color: black;
  padding: 0 1em;
}
.card > p {
  margin: 0.2em;
}
@media only screen and (max-width: 1120px) {
  .card {
    width: 45%;
  }
}
@media only screen and (max-width: 600px) {
  .card {
    width: 90%;
  }
}
</style>