<template>
  <AppHeader @toggle-login-open="isLoginOpen = true" />
  <div class="w-full flex">
    <router-view></router-view>
    <!-- <Calendar /> -->
  </div>
  <LoginModal v-if="isLoginOpen" @toggle-login="isLoginOpen = false" />
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import LoginModal from "./components/LoginModal.vue";
import { getAuth, onAuthStateChanged } from "firebase/auth";
import firebase from "./utilities/firebase";

// import Calendar from "./components/Calendar.vue";
export default {
  name: "App",
  data() {
    return {
      isLoginOpen: false,
      isLoggedIn: false,
      authUser: [],
    };
  },
  components: {
    AppHeader,
    // Calendar,
    LoginModal,
  },
  emits: ["toggle-login", "toggle-login-open"],
  mounted() {
    const auth = getAuth(firebase);
    onAuthStateChanged(auth, (user) => {
      if (user) {
        // User is signed in, see docs for a list of available properties
        // https://firebase.google.com/docs/reference/js/firebase.User
        // const uid = user.uid;
        this.isLoggedIn = true;
        this.authUser = user;
        this.isLoginOpen = false;

        console.log(user);
        // ...
      } else {
        this.isLoggedIn = false;
        this.authUser = [];
        console.log("no user");
        // User is signed out
        // ...
      }
    });
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
