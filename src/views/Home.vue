<template>
  <div v-if="user">
    <About style="margin-bottom:40px;" />
    <h2>Food history for the past week</h2>
    <FoodCalendar />
  </div>
  <div v-if="!user" style="padding-top: 15vh">
    <About />
    <br><br>
    <h2>
      <router-link to="/SignIn">Sign in</router-link> to enjoy the full feature
      of our app!
    </h2>
  </div>
</template>

<script>
  import { getAuth, onAuthStateChanged } from "firebase/auth";
  import FoodCalendar from "@/components/FoodCalendar.vue";
  import About from "@/components/About.vue";

  export default {
    name: "App",
    components: {
      FoodCalendar,
      About,
    },
    data() {
      return {
        user: false,
      };
    },
    mounted() {
      const auth = getAuth();
      onAuthStateChanged(auth, (user) => {
        if (user) {
          this.user = user;
        }
      });
    },
  };
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
