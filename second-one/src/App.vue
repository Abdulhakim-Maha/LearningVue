<template>
  <AppHeader />
  <div class="w-full flex">
    <router-view></router-view>
    <!-- <Calendar /> -->
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
// import Calendar from "./components/Calendar.vue";
export default {
  name: "App",
  components: {
    AppHeader,
    // Calendar,
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
