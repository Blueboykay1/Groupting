<template>
  

<form @submit.prevent="login">
  <div class="imgcontainer">
   
    <img src="../assets/Images/user.png" alt="Avatar" class="avatar">
  </div>

  <div class="container">
    <label for="emza"><b>E-Mail</b></label>
    <input type="email" placeholder="Enter Email" v-model="email" name="email" required>

    <label for="psw"><b>Password</b></label>
    <input type="password" placeholder="Enter Password" v-model="password" name="psw" required>

    <button type="submit">Login</button>
    <label>
      <input type="checkbox" checked="checked" name="remember"> Remember me
    </label>
  </div>

   <p>
      Sign Up With Us >>> 
      <router-link :to="{ name: 'SignUp' }">Create an account</router-link>
    </p>
</form>


 
   
  

  

   




</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },

  methods: {
    login() {
      fetch("https://full-proj.herokuapp.com/User", {
        method: "PATCH",
        body: JSON.stringify({
          email: this.email,
          password: this.password,
        }),

        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })

        .then((response) => response.json())

        .then((json) => {
          console.log(json)
          localStorage.setItem("jwt", json.jwt);
          alert("User logged in");
          this.$router.push({ name: "Products" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>

<style scoped>
/* Bordered form */
form {
  border: 3px solid #f1f1f1;
}

/* Full-width inputs */
input[type=text], input[type=password], input[type=email] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

/* Set a style for all buttons */
button {
  background-color: #04AA6D;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
}

/* Add a hover effect for buttons */
button:hover {
  opacity: 0.8;
}

/* Extra style for the cancel button (red) */
.cancelbtn {
  width: auto;
  padding: 10px 18px;
  background-color: #f44336;
}

/* Center the avatar image inside this container */
.imgcontainer {
  text-align: center;
  margin: 24px 0 12px 0;
}

/* Avatar image */
img.avatar {
  width: 40%;
  border-radius: 50%;
}

/* Add padding to containers */
.container {
  padding: 16px;
}

/* The "Forgot password" text */
span.psw {
  float: right;
  padding-top: 16px;
}

/* Change styles for span and cancel button on extra small screens */
@media screen and (max-width: 300px) {
  span.psw {
    display: block;
    float: none;
  }
  .cancelbtn {
    width: 100%;
  }
}
</style>
