<template>
  <section id="projets">
    <div class="degrade"></div>
        <div class="projets">
            <p class="titreSection"> <strong>Mes projets</strong></p>
            <p class="typeProjet"> Projets Majeurs : </p>
            <div class="mesProjets" id="mesProjetsMajeurs">
                <ProjetComponent v-for="k in projet.ProjetsMajeurs" :data="k"/>
            </div>
            <div class="centrageBarre">
                <div class="barreSeparation"></div>
            </div>
            <p class="typeProjet"> Projets Mineurs :</p>
            <div class="mesProjets" id="mesProjetsMineurs">
                <ProjetComponent v-for="k in projet.ProjetsMineurs" :data="k"/>
            </div>
            <div class="centrageBarre">
                <div class="barreSeparation"></div>
            </div>
            <p class="typeProjet"> Projets Personnels : </p>
            <div class="mesProjets" id="mesProjetsPerso">
                <ProjetComponent v-for="k in projet.ProjetsPerso" :data="k"/>
            </div>
            <div class="centrageBarre">
                <div class="barreSeparation"></div>
            </div>
        </div>
    </section>
</template>

<script setup>
import ProjetComponent from '@/components/ProjetComponent.vue';
import { ref } from 'vue';

const props = defineProps(["data"]); 
const projet = ref(null); 
projet.value = props.data.Projets;
</script>

<style>
#projets {
    height: auto;
    width: auto;
    background-color: #2B2B2B;
    overflow: hidden;
}
.projets {
    height: auto;
    width: auto;
    margin-left: 4vw;
    margin-right: 4vw;
}
.typeProjet {
    font-size: 2.3vw;
    text-align: left;
    margin-left: 10vw;
    margin-top: 8vh;
    margin-bottom: 6vh;
    text-decoration: underline 2px;
}
.mesProjets {
    display: flex;
    justify-content: center;
    align-items: left;
    flex-wrap: wrap;
    column-gap: 5vw;
}

.degrade {
    width: 100%;
    height: 6vw;
    background: linear-gradient(180deg, #262626, #2b2b2b);
    margin: 0;
    padding: 0;
}
</style>