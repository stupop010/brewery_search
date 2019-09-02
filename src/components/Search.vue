/* eslint-disable */
<template>
  <div class="search-container">
    <form v-on:submit.prevent="onSubmit">
      <div class="form-group">
        <input type="text" placeholder="Search..." class="search-input" v-model="search" />
        <div>
          <button type="submit">Submit</button>
          <button v-on:click.prevent="clear">clear</button>
        </div>
      </div>
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
      if (!this.search) return;
      const res = await axios.get(
        `https://api.openbrewerydb.org/breweries/search?query=${this.search}`
      );
      this.brew = res.data;
      this.clear();
    },
    clear() {
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
.form-group {
  display: flex;
}
button {
  font-size: 1.2em;
  margin-left: 0.5em;
  border-radius: 5px;
  border: 1px solid black;
  background: grey;
}
button:hover {
  cursor: pointer;
  transform: scale(1.1);
}

@media only screen and (max-width: 620px) {
  .search-input {
    width: 100%;
  }
  .form-group {
    flex-direction: column;
  }
  .form-group > div {
    margin-top: 0.5em;
  }
}
</style>