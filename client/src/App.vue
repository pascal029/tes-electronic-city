<script>
import Navbar from "./components/Navbar.vue";
import Home from "./views/Home.vue";
import Login from "./views/Login.vue";
import User from "./views/User.vue";
import List from "./views/List.vue";
export default {
  components: {
    Navbar,
    Home,
    Login,
    User,
    List,
  },
  data() {
    return {
      currentPage: "login",
      username: "tes@eci.co.id",
      password: "tes123",
    };
  },
  created() {
    if (localStorage.access_token) {
      this.username = localStorage.username;
      this.currentPage = "home";
    } else {
      this.currentPage = "login";
    }
  },
  methods: {
    changePage(nextPage) {
      this.currentPage = nextPage;
    },
    async login(data) {
      try {
        let error = "";
        if (!data.password || !data.username) {
          error = "Username and password are required";
          throw error;
        }
        if (data.username == this.username && data.password == this.password) {
          localStorage.setItem("access_token", "ada");
          localStorage.setItem("username", this.username);
          Swal.fire("login success");
          this.changePage("home");
        } else {
          error = "Incorrect username or password";
          throw error;
        }
      } catch (error) {
        Swal.fire({
          position: "center",
          width: "15em",
          icon: "error",
          title: error,
          showConfirmButton: false,
          timer: 1500,
        });
      }
    },
  },
};
</script>

<template>
  <div class="h-screen">
    <section v-if="currentPage == 'home'">
      <Home />
    </section>
    <section v-if="currentPage == 'login'">
      <Login @login="login" />
    </section>
    <section v-if="currentPage == 'list'">
      <List />
    </section>

    <section v-if="currentPage == 'user'">
      <User />
    </section>
    <Navbar @changePage="changePage" v-if="currentPage != 'login'" />
  </div>
</template>

<style></style>
