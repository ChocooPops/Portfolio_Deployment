<script setup>
  import axios from "axios"
  import { ref } from 'vue';

  import Accueil from "./views/AccueilView.vue"
  import Profil from "./views/ProfilView.vue"
  import TechnosView from "./views/TechnosView.vue"
  import ProjetsView from "./views/ProjetsView.vue"
  import CompetencesView from "./views/CompetencesView.vue"
  import FooterView from "./views/FooterView.vue"

  let infos = ref(null);
  const getData = () => {
    axios.get('https://chocoopops.github.io/portfolio/db.json')
    .then(response => {
      infos.value = response.data
    }).catch(err => {
      console.log(err)
    })
  }
  getData()
</script>

<template>
  <body>
    <Accueil v-if = "infos != null" :data="infos[0]"/>
    <Profil />
    <TechnosView v-if = "infos != null" :data="infos[0]"/>
    <ProjetsView v-if = "infos != null" :data="infos[0]"/>
    <CompetencesView v-if = "infos != null" :data="infos[0]"/>
    <FooterView />
  </body>
</template>

<style>
@media  screen and (max-width: 500px) {
    .titreSection {
        text-align: center;
        font-size: 5vw;
    }
}
</style>