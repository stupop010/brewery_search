/* eslint-disable */
<template>
  <div class="search-container">
    <form v-on:submit.prevent="onSubmit">
      <input type="text" placeholder="Search..." class="search-input" v-model="search" />
    </form>
    <Results :brew="brew" />
  </div>
</template>

<script>
import axios from "axios";
import Results from "./Results.vue";

export default {
  name: "Search",
  components: {
    Results
  },
  data() {
    return {
      search: "",
      brew: []
    };
  },
  methods: {
    async onSubmit() {
      const res = await axios.get(
        `https://api.openbrewerydb.org/breweries/search?query=${this.search}`
      );
      this.brew = res.data;
      this.search = "";
    }
  },
  async created() {
    const res = await axios.get("https://api.openbrewerydb.org/breweries");
    this.brew = res.data;
  }
};
</script>

<style scoped>
.search-container {
  height: 4em;
  width: 80%;
  margin: 0 auto;
  margin-top: 2em;
}
.search-input {
  font-size: 1.7em;
  padding-left: 0.2em;
  width: 12em;
  border: 1px solid black;
}
</style>