<template>
  <div>
    <div class="wrapper">
      <div class="top_navbar">
        <div class="hamburger">
          <div class="one"></div>
          <div class="two"></div>
          <div class="three"></div>
        </div>
        <div class="top_menu">
          <div class="logo">3Gags</div>
          <ul>
            <li>
              <a href="#">
                <i class="fas fa-search"></i>
              </a>
            </li>
            <li>
              <a href="#">
                <i class="fas fa-bell"></i>
              </a>
            </li>
            <li>
              <a href="#">
                <i class="fas fa-user"></i>
              </a>
            </li>
          </ul>
        </div>
      </div>

      <div class="sidebar">
        <ul>
          <li>
            <a href="#" @click.prevent="toPublic">
              <span class="icon">
                <i class="fas fa-book" aria-hidden="true"></i>
              </span>
              <span class="title">Publics</span>
            </a>
          </li>
          <li>
            <a href="#">
              <span class="icon">
                <i class="far fa-images" aria-hidden="true"></i>
              </span>
              <span class="title">add Picture</span>
            </a>
          </li>
          <li @click.prevent="logout">
            <a href="#">
              <span class="icon">
                <i class="fas fa-sign-out-alt" aria-hidden="true"></i>
              </span>
              <span class="title">Logout</span>
            </a>
          </li>
        </ul>
      </div>

      <div class="main_container">
        <div class="item">
          <div class="content-title">
            <h4>Add New Picture</h4>
          </div>
          <div class="content">
            <form>
              <h1>Title</h1>
              <input type="text" id="pic-title" />
              <input type="file" name="pic" accept="image/*" />
              <input @click="addData()" value="Upload Picture" />
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Axios from "axios";

export default {
  data: function() {
    return {};
  },
  methods: {
    addData() {
      Axios({
        url: `http://35.240.175.171/meme/add`,
        methods: "POST",
        data: {
          title,
          img
        },
        headers: localStorage.token
      })
        .then(function() {
          console.log("success");
        })
        .catch(function(err) {
          console.log(err);
        });
    },
    logout() {
      this.$emit("logout");
    },
    toPublic() {
      this.$emit("toPublic");
    },
    components: {},
    created: {}
  },
  components: {}
};
</script>


<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,600,700&display=swap");
* {
  margin: 0;
  padding: 0;
  list-style: none;
  text-decoration: none;
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}

body {
  background: #ffffff;
}

.wrapper {
  margin: 0px;
  padding: 0px;
}

.wrapper .top_navbar {
  /* width: calc(100% - -5px); */
  width: 100%;
  height: 60px;
  display: flex;
  position: fixed;
  top: 0px;
}

.wrapper .top_navbar .hamburger {
  width: 70px;
  height: 100%;
  background: #2e4ead;
  padding: 15px 17px;
  border-top-left-radius: 0px;
  cursor: pointer;
}

.wrapper .top_navbar .hamburger div {
  width: 35px;
  height: 4px;
  background: #92a6e2;
  margin: 5px 0;
  border-radius: 0px;
}

.wrapper .top_navbar .top_menu {
  width: calc(100% - 70px);
  height: 100%;
  background: #fff;
  border-top-right-radius: 0px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
}

.wrapper .top_navbar .top_menu .logo {
  color: #2e4ead;
  font-size: 20px;
  font-weight: 700;
  letter-spacing: 3px;
}

.wrapper .top_navbar .top_menu ul {
  display: flex;
}

.wrapper .top_navbar .top_menu ul li a {
  display: block;
  margin: 0 10px;
  width: 35px;
  height: 35px;
  line-height: 35px;
  text-align: center;
  border: 1px solid #2e4ead;
  border-radius: 0%;
  color: #2e4ead;
}

.wrapper .top_navbar .top_menu ul li a:hover {
  background: #4360b5;
  color: #fff;
}

.wrapper .top_navbar .top_menu ul li a:hover i {
  color: #fff;
}

.wrapper .sidebar {
  position: fixed;
  top: 60px;
  left: 0px;
  background: #2e4ead;
  width: 200px;
  height: calc(100% - 40px);
  border-bottom-left-radius: 0px;
  transition: all 0.3s ease;
}

.wrapper .sidebar ul li a {
  display: block;
  padding: 20px;
  color: #fff;
  position: relative;
  margin-bottom: 1px;
  color: #92a6e2;
  white-space: nowrap;
}

.wrapper .sidebar ul li a:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 3px;
  height: 100%;
  background: #92a6e2;
  display: none;
}

.wrapper .sidebar ul li a span.icon {
  margin-right: 10px;
  display: inline-block;
}

.wrapper .sidebar ul li a span.title {
  display: inline-block;
}

.wrapper .sidebar ul li a:hover,
.wrapper .sidebar ul li a.active {
  background: #4360b5;
  color: #fff;
}

.wrapper .sidebar ul li a:hover:before,
.wrapper .sidebar ul li a.active:before {
  display: block;
}

.wrapper .main_container {
  height: 560px;
  background: #e1ecf2;
  width: (100% - 200px);
  margin-top: 70px;
  margin-left: 300px;
  margin-right: 100px;
  padding: 40px;
  transition: all 0.3s ease;
}

.wrapper .main_container .item {
  background: #fff;
  margin-bottom: 50px;
  padding: 20px;
  font-size: 14px;
  line-height: 22px;
}

.wrapper .main_container .footer-content {
  border-top: 2px;
  display: flex;
  margin-top: 15px;
  padding: 15px;
}

#share-buttons img {
  background-color: #4360b5;
  padding: 5px;
  border: 0;
  box-shadow: 0;
  display: flex;
  margin-left: 10px;
}

.wrapper.collapse .sidebar {
  width: 70px;
}

.wrapper.collapse .sidebar ul li a {
  text-align: center;
}

.wrapper.collapse .sidebar ul li a span.icon {
  margin: 0;
}

.wrapper.collapse .sidebar ul li a span.title {
  display: none;
}

.wrapper.collapse .main_container {
  width: (100% - 70px);
  margin-left: 70px;
}

.item {
  display: flex;
  flex-direction: column;
}
</style>