<template>
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
  <table v-for="contact in fiveActors" :key="contact.id">
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
import contacts from '../contacts.json';
export default {
    name: 'ActorsList',
    data () {
    return {
      contacts: contacts,
      fiveActors: [],
    };
  },

  created() {
    for (let i = 0; i < 5; i++) {
        this.fiveActors.push(this.contacts.shift());
    }
  },

  methods: {
     randomActor() {
      const restOfList = this.contacts.splice(5, contacts.length);
      this.fiveActors.unshift(restOfList[0]);
      this.fiveActors.splice(Math.floor(Math.random() * this.contacts.slice(5)), 1);
    },
    mostPopular() {
      this.fiveActors.sort((a,b) => a.popularity > b.popularity ? 1 : -1);
    },
    alphaSort() {
      this.fiveActors.sort((a,b) => a.name > b.name ? 1 : -1);
    } 

  }

}
</script>
