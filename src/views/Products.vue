<template>
<div v-for="product of products" :key="product.name" class="card" style="width: 25rem;">
  <img :src="product.img" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">{{product.name}}</h5>
    <p class="card-text">R{{product.price}}</p>
    <p class="card-text">{{product.category}}</p>
    <router-link to="/cart" class="login btn btn-primary text-white">Add to cart</router-link>
  </div>
</div>

  
</template>

<script>
export default {
  data() {
    return {
      products: null,
      isLoggedIn: true
    };
  },
  // fetching product
  mounted() {
    console.log(localStorage.getItem("jwt"));
    if (localStorage.getItem("jwt")) {
      fetch("https://full-proj.herokuapp.com/Product", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.products = json;
          this.products.forEach(async (product) => {
            await fetch(
              "https://full-proj.herokuapp.com/Product" + product.name,
              {
                method: "GET",
                headers: {
                  "Content-type": "application/json; charset=UTF-8",
                  Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                },
              }
            )
              .then((response) => response.json())
              .then((json) => {
                product.name = json.name;
              });
          });
        })
        .catch((err) => {
          alert("Cannot get products");
          // this.$router.push({name: "Login"})
        });
    } else {
      alert("Not logged in");
      this.$router.push({ name: "Login" });
    }

  },
}
</script>

<style>

</style>