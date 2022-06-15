<template>
  <div
    class="container mx-auto bg-indigo-50 flex flex-col items-center justify-center text-3xl font-bold text-indigo-500 uppercase"
  >
    <p>count {{ count }}</p>
    <button
      @click="toggle = !toggle"
      class="w-20 h-10 bg-indigo-500 rounded-md"
    ></button>
  </div>
  <!-- display condition -->
  <div class="container text-center bg-indigo-200 mx-auto">
    <div class="" v-if="toggle">
      <h1>{{ post.userId }}</h1>
      <h2>{{ post.id }}</h2>
      <p>{{ post.title }}</p>
    </div>
  </div>
  <!-- <HelloWorld /> -->
  <!-- <Header title="42"/> -->
  <div class="container mx-auto flex justify-center items-center flex-col">
    <p>message is:{{ message }}</p>
    <input
      class="border-spacing-1 p-2 bg-indigo-100 rounded"
      type="text"
      v-model="message"
      placeholder="edit me"
    />
  </div>
  <div>Checked names: {{ checkedNames }}</div>

  <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
  <label for="jack">Jack</label>

  <input type="checkbox" id="john" value="John" v-model="checkedNames" />
  <label for="john">John</label>

  <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
  <label for="mike">Mike</label>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Header from "./components/Header.vue";

export default {
  components: {
    Header,
    HelloWorld,
  },
  data() {
    return {
      count: 0,
      toggle: Boolean,
      message: "",
      checkedNames: [],
      post: {
        type: Object,
      },
    };
  },
  methods: {
    increment() {
      this.count++;
    },
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/posts/1")
      .then((res) => res.json())
      .then((data) => this.post = data);
  },
};
</script>
