<template>
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
  computed: {
     randomActor() {
      const randomActor = Math.floor(Math.random() * contacts.slice(5));
      contacts.slice(5).splice(randomActor, 1);
    },
    mostPopular() {
      this.contacts.slice(0,5).sort((a,b) => a.popularity > b.popularity);
    },
    alphaSort() {
      this.contacts.slice(0,5).sort((a,b) => a.name > b.name);
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

button {
  margin: 8px;

}

.header, table {
  margin: 10px 100px;
}

td {
  padding-left: 3em;
}

</style>
