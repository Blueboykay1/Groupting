<template>
  <div class="body">


  <img class="hero-image" src="../assets/Images/wally.jpg" alt="" srcset="">
  <div class="hero-text">
    <h1 style="font-size:50px">Welcome To AUTHENTIC ALBUMS</h1>
    <p>Buy music albums with us</p>
    <a href="/login">SHOP</a>
  </div>



</div>
  
</template>

<script>


export default {
  name: 'Home',
  components: {
    
  }
}
</script>
<style>
.body, html {
  height: 100%;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.hero-image {
  background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5));
  height: 50%;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  position: relative;
}

.hero-text {
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: AQUA;
}

.hero-text a {
  border: none;
  outline: 0;
  display: inline-block;
  padding: 10px 25px;
  color: black;
  background-color: #ddd;
  text-align: center;
  cursor: pointer;
}

.hero-text a:hover {
  background-color: #555;
  color: white;
}
</style>
