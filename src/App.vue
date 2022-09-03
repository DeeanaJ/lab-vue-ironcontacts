<template>
  <h1>IronContacts</h1>
  <ActorsList />
</template>

<script>  
import ActorsList from './components//ActorsList.vue';

export default {
  name: "App",
  components: {ActorsList}
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
