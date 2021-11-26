<template>
  <div class="contain">
    <div class="wrap">
      <img :src="img_src" alt="" class="img_avt" />
      <button @click="toggleVisible">Detail</button>
      <!-- v-show แสดงหรือซ่อน ก็คือ style="none"  -->
      <article v-show="isVisible" class="article"> 
        <h3>{{ getFullName }}</h3>
        <h3>Age : {{ age }}</h3>
        <p>Address : {{ address }}</p>
        <p>Contact : <a :href="github" target="_blank">Github</a></p>
        <p v-if="hobby.length === 0">No hobby</p>
        <div v-else>
          <p>Hobby</p>
          <ul>
            <!-- for loop -->
            <li v-for="(item, idx) in hobby" :key="idx">{{ item }}</li>
          </ul>
        </div>
      </article>
      <!-- if else  -->
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstname: "austiniqer",
      age: 19,
      address: "Lardkrabang, Bangkok",
      img_src: "https://avatars.githubusercontent.com/u/69495813?v=4",
      github: "https://github.com/Abdulhakim-Maha",
      isVisible: false,
      hobby: ["programming", "game", "watching youtube", "sleeping"],
    };
  },
  methods: {
    toggleVisible() {
      this.isVisible = !this.isVisible;
    },
  },
  computed: {
   getFullName(){
     return `${this.firstname} maha`
   } 
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0 auto;
  box-sizing: border-box;
}
.contain {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  width: 100vw;
  height: 100vh;
  /* background-color: bisque; */
}
.wrap {
  width: 50%;;
  height: 50%;
  display: flex;
  flex-direction: column;
  padding: 3rem;
  border-radius: 10px;
  border : 1px solid gray;
}
button{
  margin-top: 5px;
  background-color: bisque;
  width: 100px;
  height: 50px;
  border-radius: 10px;
  cursor: pointer;
}
.img_avt {
  width: 90px;
  height: 90px;
  border-radius: 50%;
}
a {
  text-decoration: none;
  color: blue;
}
</style>
