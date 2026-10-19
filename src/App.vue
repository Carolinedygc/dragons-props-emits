<script setup>
import dragonData from './assets/js/dragons';
import { ref } from 'vue';
import Dragon from './compontents/Dragon.vue';

// state
const dragons = ref(dragonData)


</script>

<template>

  <!-- 10. Gør nu sådan at når I ændrer dragens navn i childcomponent, bliver det opdateret i App.vue. Se de næste fem trin (11-15) -->

  <!-- 11. Lav state der holder hvad dragens nye navn er og bind dette til input i <form> -->

  <!-- 12. Opsæt nu en defineEmit macro og find på et custom event-navn der om lidt skal bruges -->

  <!-- 13. Sørg for at form har en eventlistener der lytter efter submit og sørger for ikke at opdatere siden, hvordan gør man det? Når der submittes kaldes en funktion -->

  <!-- 14.  I funktionen skal der emittes den event vi har navngivet, sørg for at medsende det nye navn OG id -->

  <!-- 15: I App.vue skal der lyttes efter det nye custom event, laves en funktion der tager imod det nye navn og id og opdaterer den rigtige drage  -->

  <!-- 16. Ekstra/evt: lav en mulighed for at delete dragerne i DragonComp. Så de sender en anden custom event og App.vue fjerner den relevante drage fra state - hjælp i de kommende trin. Se her: https://youtu.be/uXvypD2gPjw -->

  <!-- 17. Opsæt en deleteknap og opsæt eventlistener på den der kalder en funktion: handleDelete -->

  <!-- 18. handleDelete skal emitte en custom event (deleteDragon) OG sende dragens ID som payload -->

  <!-- 19. I app.vue skal DragonComp nu lytte efter deleteDragon eventet og håndtere dette. Den skal bruge id'et fra den drage der skal slettes og slette den rigtige drage i listen med drager i state i App.vue. Her kan man anvende .filter() metoden -->

  <header>
    <h1>D&D website</h1>
    <h2>
      Your source for DnD dragons. Providing dragon information since 2021.<br />
      Find info about <span>{{dragons.length}}</span> dragons here.
    </h2>
  </header>
  <main>
   <dragon :dragonProps="dragon" v-for="dragon in dragons" :key="dragon.id"
         
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
