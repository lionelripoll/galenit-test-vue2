<template>
<div>

  <div class="container-fluid">
    <div class="row">

      <div class="col-md-2">Side menu</div>

      <div class="col-md-10">
        <h1>{{ title }}</h1>
        <h3>Message from backend: {{ message }}</h3>
        <button type="button" class="btn btn-primary">bootstrap button</button>
      </div>

    </div>
  </div>

</div>
</template>

<script>
import axios from 'axios'

window.axios = require("axios");

export default {
  name: 'Distributors',

  components: {

  },
  data() {
    return {
      title: "Hello Distributor",
      message: null,
    };
  },
  mounted() {
    axios
      .get("http://138.197.136.237:8081/hello")
      .then(response => (this.message = response.data));
  }
};
</script>

<style>

</style>
