<template>
  <div class="login">
    <h1>Login</h1>
    <p>(づ｡◕‿‿◕｡)づ</p>
    <input v-model="user.email" type="text" placeholder="Enter Email" />
    <input v-model="user.password" type="password" placeholder="Enter Password" />
    <button class="btn-login" @click.prevent="login">Login</button>
    <a @click.prevent="toRegister">register</a>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      user: {
        email: "",
        password: ""
      },
      server: `http://35.240.175.171`
    };
  },
  methods: {
    login() {
      axios({
        method: "post",
        url: `${this.server}/user/login`,
        data: {
          email: this.user.email,
          password: this.user.password
        }
      })
        .then(({ data }) => {
          localStorage.setItem("token", data.token);
          this.$emit("tomainpage");
        })
        .catch(err => {
          Swal.fire({
            type: "error",
            title: "Oops...",
            text: `${err.response.data.message}`
          });
        });
    },
    toRegister() {
      this.$emit("toRegister");
    }
  }
};
</script>

<style>
.login {
  background-color: rgba(255, 255, 255, 0.445);
  height: 500px;
  width: 400px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border-radius: 15px;
  box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.18);
}

.login h1 {
  font-size: 30px;
  letter-spacing: 5px;
  font-family: "Indie Flower", cursive;
  text-align: center;
  border-bottom: 2px solid black;
}

.login input {
  margin: 5px;
  padding: 15px 70px 15px 5px;
  border: none;
  border-bottom: 0.6px solid rgb(90, 90, 90);
}

.btn-login {
  padding: 9px 20px;
  border: none;
  background-color: rgb(12, 12, 12);
  color: white;
  cursor: pointer;
  transition: 300ms;
  text-align: center;
}

.btn-login:hover {
  padding: 11px 22px;
  box-shadow: 5px 5px 1px 0px rgba(0, 0, 0, 0.18);
}

.login a {
  color: rgb(68, 15, 241);
  margin-left: 75%;
  cursor: pointer;
  text-decoration: underline;
}
</style>