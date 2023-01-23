<script>
import Navbar from './components/Navbar.vue'
import Home from './views/Home.vue'
import Login from './views/Login.vue'
import User from './views/User.vue'
import List from './views/List.vue'
export default {
  components : {
    Navbar,
    Home,
    Login,
    User,
    List
  },
  data(){
    return {
      currentPage : 'login',
      username : ''
    }
  },
  created () {
    if(localStorage.access_token){
      this.username = localStorage.username
      this.currentPage = 'home'
    }else {
      this.currentPage='login'
    }
  },
  methods : {
    changePage(nextPage) {
      this.currentPage = nextPage
    }
  }
}
</script>

<template>
  <div v-if="currentPage != 'login'">
    <Navbar />
  </div>
  <section v-if="currentPage == 'home'">
    <Home />
  </section>
  <section v-if="currentPage == 'login'">
    <Login />
  </section>
  <section v-if="currentPage == 'list'">
    <List />
  </section>

  <section v-if="currentPage == 'user'">
    <User />
  </section>
</template>

<style>
</style>
