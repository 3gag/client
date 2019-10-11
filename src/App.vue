<template>
  <div>
    <div class="container">
      <login
        v-if="page === 'login'"
        @toRegister="changePages('register')"
        @tomainpage="changePages('mainpage')"
      ></login>
      <register
        v-if="page === 'register'"
        @toLogin="changePages('login')"
        @tomainpage="changePages('mainpage')"
      ></register>
      <pictureform
        @toPublic="changePages('mainpage')"
        @logout="logout"
        v-if="page === `pictureFrom`"
      ></pictureform>
    </div>
    <mainpage
      @logout="logout"
      @toPictureFrom="changePages('pictureFrom')"
      v-if="page === 'mainpage'"
    ></mainpage>
  </div>
</template>

<script>
import login from "./components/login";
import register from "./components/register";
import mainpage from "./components/mainPage";
import pictureform from "./components/pictureForm";

export default {
  components: {
    login,
    register,
    mainpage,
    pictureform
  },
  data() {
    return {
      page: "login"
    };
  },
  methods: {
    changePages(page) {
      this.page = page;
    },
    logout() {
      localStorage.removeItem("token");
      this.page = "login";
    }
  },
  created() {
    if (localStorage.getItem("token")) {
      this.page = "mainpage";
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