<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h1>IronContacts</h1>
  <div class="btns">
    <button @click="randomActor">Add Random Contact</button>
    <button @click="mostPopular">Sort by Popularity</button>
    <button @click="alphaSort">Sort by Name</button>

  </div>

  <div class="header">
    <p>Picture</p>
    <p>Name</p>
    <p>Popularity</p>
    <p>Won Emmy</p>
    <p>Won Oscar</p>
    </div>
  <table v-for="contact in contacts.slice(0,5)" :key="contact.id">
    <tr>
    <td><img class="pics" :src="contact.pictureUrl"></td>
    <td>{{ contact.name }}</td>
    <td>{{ contact.popularity.toFixed(2) }}</td>
    <td v-if="contact.wonOscar">YES</td>
    <td v-else></td>
    <td v-if="contact.wonEmmy">YES</td>
    <td v-else></td>
    
    </tr>
  </table>
  <!-- <div class="contact" v-for="contact in contacts.slice(0,5)" :key="contact.id">
    <img :src="contact.pictureUrl" alt='actor'/>
    <div>{{contact.name}}</div>
    <div>{{contact.popularity}}</div>
    <div v-if="contact.wonOscar">Won Oscar</div>
    <div v-else></div>
    <div v-if="contact.wonEmmy">Won Emmy</div>
    <div v-else></div>
  </div> -->

</template>

<script>  
import contacts from "./contacts.json";

export default {
  name: "App",
  data () {
    return {
      contacts: contacts,
    };
  },
  methods: {
     randomActor() {
    },
    mostPopular() {
      pis.contacts.slice(0,5).sort((a,b) => a.popularity > b.popularity);
    },
    alphaSort() {
      pis.contacts.slice(0,5).sort((a,b) => a.name > b.name);
    } 

  }
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smooping: antialiased;
  -moz-osx-font-smooping: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

img {
  width: 120px;
}

.header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

</style>
