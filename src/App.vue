<script setup>
import dragonData from './assets/js/dragons';
import { ref } from 'vue';
import Dragon from './compontents/Dragon.vue';

// state
const dragons = ref(dragonData)

function handleNameChange(newName, id){
//  find rigtige drage ud fra id
const correctDragon = dragons.value.find(dragon => dragon.id === id);

// opdater dens navn med newName
correctDragon.name = newName
}


function handleDeleteDragon(id){
  dragons.value = dragons.value.filter(
  dragon => dragon.id != id
)
}


</script>

<template>

  <header>
    <h1>D&D website</h1>
    <h2>
      Your source for DnD dragons. Providing dragon information since 2021.<br />
      Find info about <span>{{dragons.length}}</span> dragons here.
    </h2>
  </header>
  <main>
   <dragon 
   @nameChange="handleNameChange"
   @deleteDragon="handleDeleteDragon"
   :dragonProps="dragon" v-for="dragon in dragons" :key="dragon.id"
         
   > </dragon>

  </main>
</template>

<style scoped>
header {
  text-align: center;
  min-height: 60vh;
  background-image: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.9)),
    url("@/assets/img/bg_dragon.jpg");
  background-size: cover;
  display: grid;
  place-content: center;
  color: white;
}

h1 {
  font-size: 4rem;
}

span {
  color: crimson;
}

main {
  max-width: 1000px;
  margin: 1rem auto;
  padding: 2rem;
  box-shadow: 0 0 3px 1px rgba(0, 0, 0, 0.3);
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  border-radius: 6px;
}

@media screen and (max-width: 1050px) {
  main {
    grid-template-columns: 1fr;
    padding: 5rem;
  }
}
</style>
