<template>
  <nav
    class="w-full bg-gradient-to-r from-blue-800 to-blue-200 text-white px-4 py-2"
  >
    <router-link
      v-for="item in list"
      :key="item.to"
      class="mx-2"
      :to="item.to"
      >{{ item.title }}</router-link
    >
    <button @click="$emit('toggle-login-open')" class="mx-2">Login</button>
    <button @click="logout" class="mx-2">Logout</button>
  </nav>
</template>

<script>
import { getAuth,signOut } from "firebase/auth";
import firebase from "../utilities/firebase";
export default {
  name: "AppHeader",
  data() {
    return {
      list: [
        { title: "Dc-Hero", to: "/dc-heros" },
        { title: "Calendar", to: "/calendar" },
        { title: "Markdown", to: "/markdown" },
        { title: "Slider Carousel", to: "/slider" },
      ],
    };
  },
  methods: {
    logout() {
      const auth = getAuth(firebase);
      signOut(auth)
        .then(() => {
          // Sign-out successful.
        })
        .catch((error) => {
          console.log(error)
          // An error happened.
        });
    },
  },
};
</script>

<style></style>
