<template>
  <header v-show="user">
    <div id="logoDiv">
      <img
        id="logo"
        src="@/assets/Eatie_logo.png"
        alt=""
        @click="$router.push('/')"
      />
    </div>
    <div id="navbarDiv">
      <NavBar />
    </div>
  </header>
  <div v-if="user" style="height: 5vh"></div>
  <p id="body1">
    <router-view />
  </p>
  <footer v-if="user">
    <hr />
    &copy;2021 Eatie
  </footer>
  <img
  v-if="!user"
    id="notSignedInBackground"
    src="~@/assets/sign-out-background.jpg"
    alt=""
  />
</template>

<script>
  import NavBar from "./components/NavBar.vue";
  import { getAuth, onAuthStateChanged } from "firebase/auth";

  export default {
    name: "App",
    components: {
      NavBar,
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
  }

  header {
    width: 100%;
    height: 10vh;
    text-align: right;
    display: flex;
    background-color: #f1f1f1;
    top: 0;
    left: 0;
    position: fixed;
    z-index: 1;
    /* background-image: url('~@/assets/food-background.png'); */
    /* background-image: url("~@/assets/food-backgrounds.jpg"); */
    border-bottom: 5px solid rgb(15, 44, 4);
    /* background-image: url(https://assets.loseit.com/website/home/Wave.png), linear-gradient(280deg, rgb(150, 180, 169) 0, rgb(150, 180, 169) 100%); */
    /* background-size: 100% 100%; */
  }

  #body1 {
    min-height: 75vh;
  }

  body {
    background-color: #f1f1f1;
    /* background-color: rgb(170,226,205); */
    /* background-image: url(https://assets.loseit.com/website/home/Wave.png), linear-gradient(60deg, rgb(150, 180, 169) 0, rgba(246, 146, 29, 1) 100%); */
    /* background-size: 100% 100%; */
    background-image: url('~@/assets/food-backgrounds.jpg');
    /* background-size: auto cover; */
    /* background-repeat: no-repeat;
    background-position: center center; */
  }

  footer {
    margin-top: 5vh;
  }

  hr {
    height: 3px;
    width: 80%;
    border-color: black;
    background-color: black;
  }

  .h2 {
    font-size: 30px;
  }

  .h3 {
    font-size: 24px;
  }

  button {
    width: 30%;
    border-radius: 10px;
    color: rgba(17, 94, 17, 0.603);
    border: 2px solid rgba(17, 94, 17, 0.603);
  }

  button:hover {
    background-color: rgba(17, 94, 17, 0.603);
    color: white;
    box-shadow: 3px 3px grey;
    cursor: pointer;
  }

  .redButton {
    color: rgba(172, 37, 37, 0.863);
    border: 2px solid rgba(172, 37, 37, 0.863);
  }

  .redButton:hover {
    background-color: rgba(172, 37, 37, 0.863);
    color: white;
    box-shadow: 3px 3px grey;
    cursor: pointer;
  }

  #logo {
    float: left;
    height: 80%;
    cursor: pointer;
  }

  #logo:hover {
    cursor: pointer;
  }

  #logoDiv {
    width: 20%;
    margin-left: 10%;
    margin-right: 0%;
  }

  #navbarDiv {
    width: 50%;
    margin-left: 10%;
    /* margin-right: 5%; */
    margin-top: 25px;
    align-content: right;
  }

  #flex-container {
    display: flex;
    flex-wrap: wrap;
  }

  #flex-child {
    flex: 1;
    align-content: center;
    align-items: center;
  }

  #image-container {
    justify-content: center;
  }

  #flex-child:first-child {
    margin-right: 20px;
    align-content: center;
    align-items: center;
  }

  .container {
    /* background-color: #f1f1f1; */
    background-color: rgb(170, 226, 205);
    /* background-color: rgb(150, 180, 169); */
    box-shadow: 8px 8px;
    margin: 0px 150px 0px 150px;
    padding: 20px;
    border: 2.5px solid #858484;
    opacity: 0.9;
  }

  .foodIcon {
    width: 70px;
    height: 70px;
  }

  #notSignedInBackground {
    /* opacity: 0.5; */
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    position: absolute;
    z-index: -1;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
</style>
