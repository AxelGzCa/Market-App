<template>
<div class="about">
  <h1>This is an about page</h1>
  <div>
    <div  :key="index" v-for="(p,index) in result">
    <h3>{{p.title}}</h3>
    <img :src="p.thumbnail " alt="">
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
