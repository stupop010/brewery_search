<template>
  <div class="container">
    <div class="flex">
      <div class="card" v-for="brew in breweries" :key="brew.id">
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
import axios from "axios";
export default {
  name: "HelloWorld",
  data() {
    return {
      breweries: null
    };
  },
  async created() {
    const res = await axios.get("https://api.openbrewerydb.org/breweries");
    this.breweries = res.data;
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
  /* height: 10em; */
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
  overflow: scroll;
}
.card > p {
  margin: 0.2em;
}
</style>

//  url https://sandbox-api.brewerydb.com/v2/breweries
//  api d528f7e9d925d4fd60cda291a485e8bd