<template>
  <div class="abouttwo">
    <h1>This is a search result page.</h1>
    <form class="search-product" @submit.prevent="searchProduct">
      <b-form-group
        id="label-search"
        label="Search:  "
        label-for="input-search"
        description="...."
      >
        <b-form-input
          id="imput-search"
          v-model="search"
          type="text"
          placeholder="...."
        ></b-form-input>
        <b-button type="submit" variant="primary">Search</b-button>
      </b-form-group>
    </form>
    <b-card-group deck>
      <b-card
        :img-src="p.thumbnail"
        img-alt=""
        img-top
        style="max-widht: 15rem"
        body-bg-variant="info"
        border-variant="dark"
        text-variant="white"
      >
      </b-card>
    </b-card-group>
    <b-row>
      <b-col cols="12" md="6" lg="6">
        <p><b>Description</b></p>
      </b-col>
      <b-col cols="12" md="6" lg="2">
        <p><b>Price</b></p>
      </b-col>
      <b-col cols="12" md="6" lg="4">
        <p><b>Image</b></p>
      </b-col>
    </b-row>
    <div :key="index" v-for="(p, index) in result">
      <b-row>
        <b-col cols="12" md="6" lg="6">
          <p>{{ p.title }}</p>
        </b-col>
        <b-col cols="12" md="6" lg="2">
          <p>${{ p.price }}</p>
        </b-col>
        <b-col cols="12" md="6" lg="4">
          <img v-bind:src="p.thumbnail" width="90px" height="90px" alt="" />
        </b-col>
      </b-row>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "Grid",
  data: () => ({
    result: null,
  }),
  created() {
    axios
      .get("https://api.mercadolibre.com/sites/MLA/search?q=Motorola")
      .then((result) => {
        this.result = result.data.results;
      });
  },
  methods: {
    searchProduct(event) {
      event.preventDefault();
    },
  },
};
</script>
