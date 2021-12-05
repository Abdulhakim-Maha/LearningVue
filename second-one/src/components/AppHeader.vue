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
  </nav>
</template>

<script>
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
};
</script>

<style></style>
