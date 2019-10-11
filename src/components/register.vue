<template>
  <div class="register">
    <h1>register</h1>
    <p>(ง'̀-'́)ง</p>
    <input v-model="user.name" type="text" placeholder="Enter Name" />
    <input v-model="user.email" type="text" placeholder="Enter Email" />
    <input v-model="user.password" type="password" placeholder="Enter Password" />
    <button @click.prevent="register" class="btn-register">register</button>
    <a @click.prevent="toLogin">Login</a>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      user: {
        name: "",
        email: "",
        password: ""
      },
      server: `http://localhost:3000`
    };
  },
  methods: {
    toLogin() {
      this.$emit("toLogin");
    },
    register() {
      axios({
        method: "post",
        url: `${this.server}/user/register`,
        data: {
          name: this.user.name,
          email: this.user.email,
          password: this.user.password
        }
      })
        .then(({ data }) => {
          localStorage.setItem("token", data.token);
          this.$emit("tomainPage");
        })
        .catch(err => {
          Swal.fire({
            type: "error",
            title: "Oops...",
            text: `${err.response.data.message}`
          });
        });
    }
  }
};
</script>

<style>
.register {
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

.register h1 {
  font-size: 30px;
  letter-spacing: 5px;
  font-family: "Indie Flower", cursive;
  text-align: center;
  border-bottom: 2px solid black;
}

.register p {
  font-size: 40px;
}

.register input {
  margin: 5px;
  padding: 15px 70px 15px 5px;
  border: none;
  border-bottom: 0.6px solid rgb(90, 90, 90);
}

.btn-register {
  padding: 9px 20px;
  border: none;
  background-color: rgb(12, 12, 12);
  color: white;
  cursor: pointer;
  transition: 300ms;
  text-align: center;
}

.btn-register:hover {
  padding: 11px 22px;
  box-shadow: 5px 5px 1px 0px rgba(0, 0, 0, 0.18);
}

.register a {
  color: rgb(68, 15, 241);
  margin-left: 75%;
  cursor: pointer;
  text-decoration: underline;
}
</style>