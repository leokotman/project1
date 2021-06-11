<template>
  <div id="app">
    <header>
      <h1>Vue course goals</h1>
    </header>
    <section
      id="user-goal"
      class="card"
      v-on:click="selectCard('A')"
      v-bind:class="{ cardActive: cardASelected }"
    >
      <h2>course goals</h2>
      <p>{{ courseGoal }}</p>
    </section>
    <section
      class="card"
      v-bind:class="{ cardActive: cardBSelected }"
      v-on:click="selectCard('B')"
    >
      <h2>My name: {{ fullName }}</h2>
      <p>My age: {{ age }}</p>
      <p>{{ age + 5 }} in 5 years</p>
      <p>Favourite random number: {{ favouriteRandomNumber }}</p>
      <div>
        <img :src="imgLink" alt="cool cat" width="300" />
      </div>
      <h3>Set name</h3>
      <input type="text" v-on:input="setName" />
      <h3>Set Last name</h3>
      <input type="text" v-on:input="setLastName" />
      <form v-on:submit.prevent="unSubmitForm">
        <input type="text" v-model="form" />
        <button>Unsubmit</button>
      </form>
    </section>
    <section
      class="card"
      v-bind:class="{ cardActive: cardCSelected }"
      v-on:click="selectCard('C')"
    >
      <h3>Counting to 37</h3>
      <button v-on:click="add(5)">Add 5</button>
      <button v-on:click="add(1)">Add 1</button>
      <button v-on:click="reset">Reset</button>
      <p>Result: {{ result }}</p>
    </section>
    <section class="card">
      <p>You can style the paragraph, typing "user1" or "user2" below:</p>
      <input type="text" v-model="paragrStyle" />
      <p v-bind:class="paragrClasses">
        Style me!
      </p>
      <button v-on:click="toggleVisibility">Toggle Paragraph</button>

      <!-- 3) Add dynamic inline styling to the below paragraph and let the user enter a background-color -->
      <input type="text" />
      <p>Style me inline!</p>
    </section>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      courseGoal: "Finish Vue Course",
      name: "",
      lastName: "",
      age: 28,
      favouriteRandomNumber: Math.random(),
      imgLink: "https://cdn.wallpapersafari.com/59/40/rvKmOG.jpg",
      form: "",
      resultNum: 0,
      resultMsg: "",
      cardASelected: false,
      cardBSelected: false,
      cardCSelected: false,
      paragrStyle: "",
      user1style: false,
      user2style: false,
      paragrInvisibility: false,
    };
  },
  computed: {
    fullName() {
      if (this.name === "" || this.lastName === "") {
        return "";
      } else {
        return this.name + " " + this.lastName;
      }
    },
    result() {
      if (this.resultNum < 37) {
        return "Not there yet";
      } else if (this.resultNum > 37) {
        return "Too much";
      } else {
        return this.resultNum;
      }
    },
    paragrClasses() {
      return {
        user1: this.user1style,
        user2: this.user2style,
        hidden: this.paragrInvisibility,
        visible: !this.paragrInvisibility,
      };
    },
  },
  watch: {
    // will work any time 'result' output changes
    result() {
      const objThis = this;
      setTimeout(function() {
        objThis.resultNum = 0;
      }, 5000);
    },
    paragrStyle() {
      const objThis = this;
      if (objThis.paragrStyle == "user1") {
        return (objThis.user1style = true), (objThis.user2style = false);
      } else if (objThis.paragrStyle == "user2") {
        return (objThis.user2style = true), (objThis.user1style = false);
      } else {
        return (objThis.user2style = false), (objThis.user1style = false);
      }
    },
  },
  methods: {
    setName(event) {
      this.name = event.target.value;
    },
    setLastName(event) {
      this.lastName = event.target.value;
    },
    unSubmitForm() {
      alert("Form is (un)submitted! No page refresh. You typed: " + this.form);
    },
    add(number) {
      console.log("added" + number);
      this.resultNum += number;
    },
    reset() {
      this.resultNum = 0;
    },
    selectCard(card) {
      console.log(`card ${card} selected`);
      if (card === "A") {
        this.cardASelected = !this.cardASelected;
      } else if (card === "B") {
        this.cardBSelected = !this.cardBSelected;
      } else {
        this.cardCSelected = !this.cardCSelected;
      }
    },
    toggleVisibility() {
      return (this.paragrInvisibility = !this.paragrInvisibility);
    },
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
.card {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border: 2px dashed rgb(45, 202, 160);
  border-radius: 10px;
  box-sizing: border-box;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
.cardActive {
  border: 4px solid rgb(22, 95, 22);
  background-color: antiquewhite;
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

.user1 {
  background-color: blue;
  color: white;
}
.user2 {
  background-color: purple;
  color: white;
}

.visible {
  display: block;
}
.hidden {
  display: none;
}
</style>
