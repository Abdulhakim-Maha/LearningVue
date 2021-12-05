<template>
  <section
    @click="$emit('toggle-login')"
    class="z-30 h-screen w-screen bg-gray-500 fixed top-0 opacity-50"
  ></section>
  <div class="absolute inset-0">
    <div class="flex h-full">
      <div class="z-40 m-auto bg-white p-2 rounded shadow w-1/3">
        <div class="p-2 border">
          <h1 class="text-xl text-center">Login</h1>
          <form class="p-2 my-2" @submit.prevent="submitHandler">
            <div class="my-4">
              <label>Email or Username </label>
              <input
                v-model="email"
                type="email"
                placeholder="Enter your email or username."
                class="rounded shadow p-2 w-full"
              />
            </div>
            <div class="my-4">
              <label>Password</label>
              <input
                v-model="password"
                type="password"
                class="rounded shadow p-2 w-full"
                placeholder="Enter your password."
              />
            </div>
            <div class="my-4">
              <button
                type="submit"
                class="w-full rounded shadow-md p-2 bg-blue-400"
              >
                Login
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "LoginModal",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  emits: ["toggle-login"],
  methods: {
    submitHandler() {
		console.log(this.email,this.password)
	},
  },
};
</script>

<style></style>
