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
// import Calendar from "./components/Calendar.vue";
export default {
  name: "App",
  data() {
    return {
      isLoginOpen: false,
    };
  },
  components: {
    AppHeader,
    // Calendar,
    LoginModal,
  },
  emits: ["toggle-login",'toggle-login-open'],
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
