<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <header>
      <h1>Vue course goals</h1>
    </header>
    <section id="user-goal">
      <h2>course goals</h2>
      <p>{{ courseGoal }}</p>
    </section>
    <section>
      <h2>My name: {{myName}} </h2>
      <p>My age: {{ myAge }}</p>
      <p>{{ myAge + 5 }} in 5 years</p>
      <p>Favourite random number: {{ Math.random() }}</p>
      <div>
        <img :src="imgLink" alt="cool cat" width="300" />
      </div>
      <input type="text" v-model="myName"/>
    </section>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: "App",
  data() {
    return {
      courseGoal: "Finish Vue Course",
      myName: "",
      myAge: 28,
      imgLink: "https://cdn.wallpapersafari.com/59/40/rvKmOG.jpg",
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
header,
#user-goal {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#user-goal {
  border: 2px solid rgb(45, 202, 160);
}
header {
  color: white;
  background-color: rgb(45, 202, 160);
}

h1,
h2 {
  text-transform: capitalize;
}
h2 {
  border-bottom: 3px solid #2c3e50;
}

#user-goal p {
  background-color: rgb(45, 202, 160);
  min-height: 1rem;
  border-radius: 10px;
}
</style>
