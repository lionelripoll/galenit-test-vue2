<template>
<div>

  <div class="container-fluid">
    <div class="row">

      <div class="col-md-2">Side menu</div>

      <div class="col-md-10">
        <h1>{{ title }}</h1>
        <vue-bootstrap4-table :rows="rows" :columns="columns" :config="config">
        </vue-bootstrap4-table>
        <h3>Message from backend: {{ message }}</h3>
        <button type="button" class="btn btn-primary">bootstrap button</button>
      </div>

    </div>
  </div>

</div>
</template>

<script>
import axios from 'axios'
import VueBootstrap4Table from 'vue-bootstrap4-table'

window.axios = require("axios");

export default {
  name: 'Clients',

  components: {
    VueBootstrap4Table
  },
  data() {
    return {
      title: "Hello Clients",
      message: null,
      rows: [{
          "id": 1,
          "name": {
            "first_name": "Vladimir",
            "last_name": "Nitzsche"
          },
          "address": {
            "country": "Mayotte"
          },
          "email": "franecki.anastasia@gmail.com",
        },
        {
          "id": 2,
          "name": {
            "first_name": "Irwin",
            "last_name": "Bayer"
          },
          "age": 23,
          "address": {
            "country": "Guernsey"
          },
          "email": "rlittle@macejkovic.biz",
        },
        {
          "id": 3,
          "name": {
            "first_name": "Don",
            "last_name": "Herman"
          },
          "address": {
            "country": "Papua New Guinea"
          },
          "email": "delia.becker@cormier.com",
        }
      ],
      columns: [{
          label: "id",
          name: "id",
          filter: {
            type: "simple",
            placeholder: "id"
          },
          sort: true,
        },
        {
          label: "First Name",
          name: "name.first_name",
          filter: {
            type: "simple",
            placeholder: "Enter first name"
          },
          sort: true,
        },
        {
          label: "Email",
          name: "email",
          sort: true,
        },
        {
          label: "Country",
          name: "address.country",
          filter: {
            type: "simple",
            placeholder: "Enter country"
          },
        }
      ],
      config: {
        checkbox_rows: true,
        rows_selectable: true,
        card_title: "Client list"
      }
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
