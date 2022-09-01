<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h1>IronContacts</h1>
  <div class="btns">
    <button @click="randomActor">Add Random Contact</button>
    <button @click="mostPopular">Sort by Popularity</button>
    <button @click="alphaSort">Sort by Name</button>

  </div>
  <section class="head">
    <h2>Picture</h2>
    <h2>Name</h2>
    <h2>Popularity</h2>
    <h2>Won Oscar</h2>
    <h2>Won Emmy</h2>
    <h2>Actions</h2>
  </section>
  
  <div class="contact" v-for="contact in firstFive" :key="contact.id">
    <img :src="contact.pictureUrl" alt='actor'/>
    <div>{{contact.name}}</div>
    <div>{{contact.popularity}}</div>
    <div v-if="contact.wonOscar">Won Oscar</div>
    <div v-else></div>
    <div v-if="contact.wonEmmy">Won Emmy</div>
    <div v-else></div>
  </div>

</template>

<script>  
import contacts from "./contacts.json";
const actors = contacts;
const firstFive = actors.slice(0,5);

export default {
  name: "App",
  methods: {
     randomActor() {
      let randomActorList = contacts.splice(5, contacts.length - 1);
      this.firstFive.unshift(randomActorList[0]);
    },
    mostPopular() {
      this.firstFive.sort((a,b) => a.popularity > b.popularity);
    },
    alphaSort() {
      this.firstFive.sort((a,b) => a.name > b.name);
    } 

  }
}
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
</style>
