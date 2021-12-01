<template>
  <AppHeader />
  <div class="w-full flex">
    <Calendar />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import Calendar from "./components/Carlendar.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    Calendar,
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
