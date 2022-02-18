<template>
<div class="about">
  <h1>This is a Mercado Libre search results page about Motorola</h1>
  <div>
    <div :key="index" v-for="(p,index) in result">
      <div class="card">
        <div class="p-3 mb-2 bg-transparent text-black card-body">
          <h3 class="fw-bold fs-4">{{p.title}}</h3>
          <h4 class="fs-6">Price: {{p.price}}</h4>
          <h5 class="fs-6">Quantity Available: {{p.available_quantity}}</h5>
          <img :src="p.thumbnail" class="rounded mx-auto d-block" alt="">
        </div>
    </div>
  </div>
</div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data: () => ({
    result: null,
  }),
  created() {
    axios.get("https://api.mercadolibre.com/sites/MLA/search?q=Motorola").then((result)=>{
      this.result=result.data.results;
    });
  }
}
</script>
