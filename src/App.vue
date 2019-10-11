<template>
  <div>
    <div class="container">
      <login
        v-if="page === 'login'"
        @toRegister="changePages('register')"
        @tomainPage="changePages('mainPage')"
      ></login>
      <register
        v-if="page === 'register'"
        @toLogin="changePages('login')"
        @tomainPage="changePages('mainPage')"
      ></register>
      <pictureForm
        @toPublic="changePages('mainPage')"
        @logout="logout"
        v-if="page === `pictureFrom`"
      ></pictureForm>
    </div>
    <mainPage
      @logout="logout"
      @toPictureFrom="changePages('pictureFrom')"
      v-if="page === 'mainPage'"
    ></mainPage>
  </div>
</template>

<script>
import login from "./components/login";
import register from "./components/register";
import mainPage from "./components/mainPage";
import pictureForm from "./components/pictureForm";

export default {
  components: {
    login,
    register,
    mainPage,
    pictureForm
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
      this.page = "mainPage";
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