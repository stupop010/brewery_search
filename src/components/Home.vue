<template>
  <div class="container">
    <div class="flex">
      <div class="card" v-for="brew in breweries" :key="brew.id">
        <h1>{{brew.name}}</h1>
        <p>{{brew.city}}</p>
        <p>{{brew.country}}</p>
        <p>{{brew.state}}</p>
        <a :href="brew.website_url" target="_blank">Website</a>
        <p>{{brew.postal_code}}</p>
        <p>{{brew.phone}}</p>
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
  background: grey;
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
  border: 1px solid black;
}
</style>

//  url https://sandbox-api.brewerydb.com/v2/breweries
//  api d528f7e9d925d4fd60cda291a485e8bd