<script setup>
import TechnoComponent from "@/components/TechnoComponent.vue"; 
import { ref } from 'vue';

const props = defineProps(["data"]); 
const techno = ref(null); 
techno.value = props.data.Technologies; 
</script>

<template>
  <section id="technologies">
    <div class="degrade2"></div>
          <div class="technologies">
              <p class="titreSection"> <strong>Les technologies que j'utilise</strong></p>
              <div class="centrageBarre">
                  <div class="barreSeparation"></div>
              </div>
              <p class="titreTechnologie">Langages de programmation : </p>
              <div class="technoListe" id="langageTechno">
                <TechnoComponent v-for="k in techno.LangageTechno" :data="k"/>
              </div>
              <div class="centrageBarre">
                  <div class="barreSeparation"></div>
              </div>
              <p class="titreTechnologie">Gestion de base de données : </p>
              <div class="technoListe" id="BDTechno">
                <TechnoComponent v-for="k in techno.BDTechno" :data="k"/>
              </div>
              <div class="centrageBarre">
                  <div class="barreSeparation"></div>
              </div>
              <p class="titreTechnologie">Environnements de développement : </p>
              <div class="technoListe" id="EnvironnementTechno">
                <TechnoComponent v-for="k in techno.EDITechno" :data="k"/>
              </div>
              <div class="centrageBarre">
                  <div class="barreSeparation"></div>
              </div>
              <p class="titreTechnologie">Frameworks : </p>
              <div class="technoListe" id="frameworkTechno">
                <TechnoComponent v-for="k in techno.FrameworkTechno" :data="k"/>
              </div>
              <div class="centrageBarre">
                  <div class="barreSeparation"></div>
              </div>
          </div>
      </section>
</template>
  
<style>
#technologies {
    height: auto;
    width: auto;
    background-color: #262626;
    overflow: hidden;
}

.technologies {
    height: auto;
    width: auto;
    margin-left: 4vw;
    margin-right: 4vw;
}

.centrageBarre {
    display: flex;
    justify-content: center;
    align-items: center;
}

.barreSeparation {
    background-color: #D9D9D9;
    height: 0.2vw;
    width: 90%;
    align-items: center;
    display: flex;
    justify-content: center;
    margin-bottom: 2vh;
}

.titreTechnologie {
    font-size: 2.3vw;
    text-align: left;
    margin-left: 3vw;
}

.technoListe {
    display: flex;
    justify-content: center;
    align-items: left;
    flex-wrap: wrap;
    row-gap: 1vw;
    column-gap: 1vw;
    margin-bottom: 2.5vw;
}

.degrade2 {
    width: 100%;
    height: 6vw;
    background: linear-gradient(180deg, #303030, #262626);
    margin: 0;
    padding: 0;
}

@media  screen and (max-width: 800px) {
    .titreTechnologie {
        font-size: 4.5vw;
        text-align: left;
        margin-left: 6vw;
    }
    .technoListe {
        display: flex;
        justify-content: center;
        align-items: left;
        flex-wrap: wrap;
        row-gap: 2vw;
        column-gap: 2vw;
        margin-bottom: 2.5vw;
    }
    .barreSeparation {
        background-color: #D9D9D9;
        height: 0.2vw;
        width: 90%;
        align-items: center;
        display: flex;
        justify-content: center;
        margin-bottom: 2vh;
        margin-top: 1.2vh;
    }
}
</style>