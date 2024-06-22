<template>
    <section id="competences">
        <div class="competences">
            <p class="titreSection">Mes Compétences</p>
            <p class="introCompetence">Mes études en IUT informatique m’ont permis d’acquérir de nombreuses compétences,
                que ce soit d’un point de vue front-end ou back-end, d’un point software ou hardware, en passant par la
                gestion et par l’organisation d’un projet.
            </p> <br>
            <div class="portefeuille" id="portefeuille">
                <CompetenceComponent v-for="k in comp" :data="k"/>
            </div>
            </div>
    </section>
</template>

<script setup>
import CompetenceComponent from '@/components/CompetenceComponent.vue';

import { ref } from 'vue';

const props = defineProps(["data"]); 
const comp = ref(null); 
comp.value = props.data.Competences; 
</script>

<style>
#competences {
    background: linear-gradient(180deg, #2B2B2B 20%, #414141 50%);
    height: auto;
    width: auto;
    overflow: hidden;
    padding-bottom: 3vw;
}
.competences {
    height: auto;
    width: auto;
    margin-left: 4vw;
    margin-right: 4vw;
    padding-bottom: 8vw;
}
.competences>p:first-child {
    margin-top: 8vw;
}
.introCompetence {
    margin-inline: 20%;
    font-size: 1.6vw;
    text-align: center;
    justify-content: center;
    word-wrap: break-word;
    margin-bottom: 4vw;
}
.portefeuille {
    height: auto;
    width: auto;
    margin-inline: 20%;
    display: flex;
    justify-content: center;
    flex-direction: column;
    overflow: hidden;
    border: solid #D9D9D9 0.3vw;
    border-radius: 0.5vw;
}
.ligneCompetence {
    height: 100%;
    width: 100%;
    display: grid;
    grid-template: 100% / 95% 5%;
    align-items: center;
    transition: 0.3s background-color;
    cursor: pointer;
}

@media  screen and (max-width: 900px) {
    .introCompetence {
        margin-inline: 5%;
        font-size: 2vw;
        text-align: center;
        justify-content: center;
        word-wrap: break-word;
        margin-bottom: 1.5vw;
    }
    .portefeuille {
        height: auto;
        width: auto;
        margin-inline: 5%;
        display: flex;
        justify-content: center;
        flex-direction: column;
        overflow: hidden;
        border: solid #D9D9D9 0.3vw;
        border-radius: 0.5vw;
    }
}
</style>