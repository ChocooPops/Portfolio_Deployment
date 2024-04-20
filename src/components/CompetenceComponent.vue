<template>
    <div class="ligneCompetence"
        @mouseover="setMouseOverComp"
        @mouseout="setMouseOutComp"
        @click="setMouseClickComp"
        :style="ligneCompetence">
        <p class="competence"> {{ comp.titre }}</p>
        <img src="../assets/img/accueil/fleche.png" alt="Mon Image" class="btCompetence" id="btCompetence1"
        @mouseover="setMouseOverFleche"
        @mouseout="setMouseOutFleche"
        :style="fleche">
    </div>
    <div class="descriptionCompetence" id="comp1"
        :style="descCompetence"
        ref="hauteurDescComp">
        <ul>
            <li v-for="k in comp.description"> {{ k }} </li>
        </ul>
    </div>
</template>

<script setup>
import { reactive, ref } from 'vue';

const props = defineProps(["data"]); 
const comp = ref(null); 
comp.value = props.data; 

const ligneCompetence = reactive({}); 
const fleche = reactive({}); 
const descCompetence = reactive({}); 
const hauteurDescComp = ref(null);

function setMouseOverComp() {
    ligneCompetence.backgroundColor = "#212121";
}
function setMouseOutComp() {
    if (hauteurDescComp.value.clientHeight <= 0) {
        ligneCompetence.backgroundColor = "transparent";
    }
}
function setMouseClickComp() {
    if (hauteurDescComp.value.clientHeight > 0) {
        descCompetence.height = "0px"; 
        fleche.transform = 'rotate(270deg)';
    } else {
        descCompetence.height = "auto"; 
        fleche.transform = 'rotate(90deg)';
    }
}

function setMouseOverFleche() {
    if (hauteurDescComp.value.clientHeight <= 0) {
        fleche.transform = 'rotate(90deg)';
    }
}

function setMouseOutFleche() {
    if (hauteurDescComp.value.clientHeight <= 0) {
        fleche.transform = 'rotate(270deg)';
    }
}

if (comp.value.id == 0) {
    ligneCompetence.borderTop = "none"
} else if (comp.value.id == comp.value.id == 5) {
    ligneCompetence.borderBottom = "none"
}
</script>

<style scoped>
.ligneCompetence {
    height: 100%;
    width: 100%;
    display: grid;
    grid-template: 100% / 95% 5%;
    align-items: center;
    transition: 0.3s background-color;
    cursor: pointer;
    border-bottom: solid #D9D9D9 0.15vw;
    border-top: solid #D9D9D9 0.15vw;
}
.btCompetence {
    max-width: 30%;
    max-height: 30%;
    height: auto;
    width: auto;
    transform: rotate(270deg);
    cursor: pointer;
    transition: 0.4s transform;
}
.descriptionCompetence {
    width: 100%;
    height: 0; /** A changer */
    margin: 0;
    padding: 0;
    overflow: hidden;
    transition: 0.4s height;
}
.descriptionCompetence>ul {
    font-size: 1vw;
    margin: 1vw;
}
</style>