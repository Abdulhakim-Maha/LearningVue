<template>
  <div class="flex flex-wrap w-full">
    <div v-for="(color, index) in sliders" :key="color" class="w-full">
      <div
        v-if="currentSlide == index"
        :class="color"
        style="height: 350px"
      ></div>
    </div>
    <div class="my-10 flex w-full">
      <div class="m-auto">
        <transition name="fade">
          <h1 v-if="isTitleShowing">Slider Carousel</h1>
        </transition>
        <button
          @click="isTitleShowing = !isTitleShowing"
          class="px-2 rounded border"
        >
          Toggle Text
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Slider",
  data() {
    return {
      currentSlide: 1,
      sliders: ["bg-purple-500", "bg-yellow-600", "bg-blue-600"],
      interval: "",
      isTitleShowing: true,
    };
  },
  mounted() {
    this.interval = setInterval(() => {
      this.currentSlide = this.currentSlide == 2 ? 0 : this.currentSlide + 1;
    }, 1000);
  },
  beforeUnmount() {
    clearInterval(this.interval);
  },
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5 ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
