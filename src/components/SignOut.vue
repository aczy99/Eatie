<template>
<button class="redButton" id = "btn" @click="signOut()" v-if="user">Logout <fa icon="sign-out-alt" /></button>
</template>

<script>
import { getAuth, onAuthStateChanged, signOut } from 'firebase/auth';

export default {
  name: "Logout",

  data() {
      return{
          user: false,
      }
  },

  mounted() {
      const auth = getAuth();
      onAuthStateChanged(auth, (user) => {
          if (user) {
              this.user = user;
          }
      })
  },

  methods: {
      async signOut() {
          const auth = getAuth();
          const user = auth.currentUser;
          signOut(auth, user)
          await this.$router.push({name:'Home'})
          window.location.reload();

      }
  }
};
</script>

<style scoped>
#btn{
    text-align: center;
    margin: auto;
}
</style>
