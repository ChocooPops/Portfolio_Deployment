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

.techno {
    height: 10vw;
    width: 16vw;
    min-width: 380px;
    min-height: 230px;
    display: grid;
    grid-template: 30% 70% / 1fr;
    border-radius: 5px;
    border: solid #363B42 3px;
    box-sizing: border-box;
    overflow: hidden;
}

.enTeteTechno {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #292B2D;
}

.enTeteTechno>p {
    font-size: 200%;
}

.enTeteTechno>img {
    max-width: 80%;
    max-height: 80%;
    height: auto;
    width: auto;
    padding-right: 15px;
}

.degrade2 {
    width: 100%;
    height: 6vw;
    background: linear-gradient(180deg, #303030, #262626);
    margin: 0;
    padding: 0;
}
</style>