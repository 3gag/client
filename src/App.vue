<template>
  <div class="container">
    <login
      v-if="page === 'login'"
      @toRegister="changePages('register')"
      @toDashboard="changePages('dashboard')"
    ></login>
    <register
      v-if="page === 'register'"
      @toLogin="changePages('login')"
      @toDashboard="changePages('dashboard')"
    ></register>
    <dashboard v-if="page === 'dashboard'"></dashboard>
  </div>
</template>

<script>
import login from "./components/login";
import register from "./components/register";
import dashboard from "./components/dashboard";

export default {
  components: {
    login,
    register,
    dashboard
  },
  data() {
    return {
      page: "login"
    };
  },
  methods: {
    changePages(page) {
      this.page = page;
    }
  },
  created() {
    if (localStorage.getItem("token")) {
      this.page = "dashboard";
    } else {
      this.page = "login";
    }
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
.container {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>