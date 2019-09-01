/* eslint-disable */
<template>
  <div class="search-container">
    <form v-on:submit.prevent="onSubmit">
      <input type="text" placeholder="Search..." class="search-input" v-model="search" />
      <p>{{search}}</p>
    </form>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      search: ""
    };
  },
  methods: {
    onSubmit() {
      console.log(this.search);
    }
  }
};
</script>

<style scoped>
.search-container {
  height: 4em;
  width: 80%;
  margin: 0 auto;
  margin-top: 1.5em;
  border: 1px solid blue;
}
.search-input {
  font-size: 1.5em;
  padding-left: 0.2em;
  border: 1px solid black;
}
</style>