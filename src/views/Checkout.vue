<template>
  <div class="container">
    <table>
      <thead>
        <tr>
          <th>product name</th>
          <th>Amount</th>
          <th>Price</th>
          <th>Delete articulo</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in items" :key="index">
          <td>{{ item.title }}</td>
          <td>{{ item.amount }}</td>
          <td>{{ item.price }}</td>
          <td>
            <button class="btn btn-warning" v-on:click="deleteItem(index)">
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      items: [],
    };
  },
  created() {
    var items_storage = localStorage.getItem("storeUT");
    if (items_storage == null) {
      this.$router.push("/about");
    }
    this.items = JSON.parse(items_storage);
    console.log(this.items);
  },
  computed: {},
  methods: {
    deleteItem(id) {
      if (window.confirm("Are you sure to delete?")) {
        console.log(id);
        this.items.splice(id, 1);
        localStorage.setItem("storeUT", JSON.stringify(this.items));
      }
    },
  },
};
</script>