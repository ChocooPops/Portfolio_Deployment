<template>
    <div class="projet" ref="projetRef">
        <div class="teteProjet"
            @mouseover="setOverTete"
            @mouseout="setOutTete"
            @click="setClickTete"
            :style="styleTete">
            <p> {{ projet.nom }} </p>
            <img src="../assets/img/projet/etoile.png">
        </div>
        <div class="tmp"></div>
        <div class="corpsImg"
            @mouseover="setOverCorpsImg"
            @mouseout="setOutCorpsImg"
            :style="styleCorpsImg">
            <div class="centrageImgProjet">
                <img :src="srcImage"
                    :style="styleImage"
                    @click="clickImage">
            </div>
        </div>
        <div class="corpsDescription"
            @mouseover="setOverCorpsDesc"
            @mouseout="setOutCorpsDesc"
            :style="styleCorpsDesc">
            <p> Description </p>
            <p> {{ projet.description }} </p>
            <button
                @mouseover="setOverButton"
                @mouseout="setOutButton"
                @click="setClickButton"
                :style="styleButton"> Télécharger </button>
        </div>
    </div>
</template>

<script setup>
import { reactive, ref, onMounted } from 'vue';

const props = defineProps(["data"]); 
const projet = ref(null); 
projet.value = props.data; 

const styleButton = reactive({}); 
const styleTete = reactive({}); 
const styleImage = reactive({}); 

function setOverButton() {
    styleButton.backgroundColor = "#222529";
}
function setOutButton() {
    styleButton.backgroundColor = "#292B2D";
}
function setClickButton() {
    window.open(projet.value.lien); 
}

function setOverTete() {
    setOverProjet(); 
}
function setOutTete() {
    setOutProjet(); 
}
function setOverCorpsImg() {
    setOverProjet(); 
}
function setOutCorpsImg() {
    setOutProjet(); 
}
function setOverCorpsDesc() {
    setOverProjet(); 
}
function setOutCorpsDesc() {
    setOutProjet(); 
}

function setOverProjet() {
    styleTete.backgroundColor = "#222529";
    styleImage.maxHeight = "90%";
    styleImage.maxWidth = "90%";
}
function setOutProjet() {
    styleTete.backgroundColor = "#292B2D";
    styleImage.maxHeight = "80%";
    styleImage.maxWidth = "80%";
}

if(projet.value.nom === "Ezougla’s Adventure") {
    styleImage.border = "none"; 
}

const projetRef = ref(null)
const styleCorpsImg = reactive({}); 
const styleCorpsDesc = reactive({}); 

let projetIsVisible = false; 
function afficherProjet() {
    styleCorpsImg.height = "100%";
    styleCorpsImg.borderRight = "none";
    styleCorpsImg.border = "solid 3px #363B42";
    styleCorpsDesc.height = "100%";
    styleCorpsDesc.border = "solid 3px #363B42";
    styleCorpsDesc.borderLeft = "none";
    projetIsVisible = true; 
}
function dissimulerProjet() {
    styleCorpsImg.height = "0";
    styleCorpsImg.borderRight = "none";
    styleCorpsImg.border = "0";
    styleCorpsDesc.height = "0";
    styleCorpsDesc.border = "none";
    styleCorpsDesc.borderLeft = "none";
    projetIsVisible = false; 
}
function setClickTete() {
    if(!projetIsVisible) {
        afficherProjet(); 
    } else {
        dissimulerProjet(); 
        projetIsVisible = false; 
    }
}

function handleScroll() {
    if (!projetRef.value) return;
    const rect = projetRef.value.getBoundingClientRect();
    const isVisible = rect.top >= 0 && rect.bottom <= window.innerHeight;
    if (isVisible) {
        afficherProjet();
    }
}
onMounted(() => {
    window.addEventListener('scroll', handleScroll);
});

const srcImage = ref(getImageUrl(projet.value.image[0])); 
let indice = 0; 
function clickImage() {
    indice ++; 
    if (indice > projet.value.image.length - 1) {
        indice = 0; 
    }
    srcImage.value = getImageUrl(projet.value.image[indice]); 
}

function getImageUrl(image) {
  return new URL(`../assets/img/projet/${image}`, import.meta.url).href;
}
</script>


<style scoped>
.projet {
    height: 387px;
    width: 603px;
    display: grid;
    grid-template: 20% 80% / 58% 42%;
    margin-bottom: 50px;
}
.teteProjet {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 32px;
    background-color: #292B2D;
    border: solid 3px #363B42;
    border-radius: 5px;
    transition: 0.3s background-color;
    cursor: pointer;
}
.teteProjet>img {
    max-width: 30%;
    max-height: 30%;
    height: auto;
    width: auto;
    object-fit: cover;
    margin-left: 15px;
    margin-bottom: 15px;
    cursor: pointer;
}
.tmp {
    height: 100%;
    width: 100%;
    background-color: transparent;
    visibility: hidden;
}
.corpsImg {
    height: 0;
    width: 100%;
    background-color: #262626;
    border-radius: 5px;
    border-right: none;
    border-top-right-radius: none;
    overflow: hidden;
    transition: 0.6s height;
    cursor: pointer;
}
.corpsDescription {
    height: 0; 
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    word-break: break-all;
    background-color: #262626;
    border-radius: 5px;
    border-left: none;
    border-top-left-radius: none;
    overflow: hidden;
    transition: 0.6s height;
}
.centrageImgProjet {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}
.centrageImgProjet>img {
    max-width: 80%;
    max-height: 80%;
    height: auto;
    width: auto;
    border: solid 5px #363B42;
    transition: 0.5s max-width, 0.5s max-height;
}
.corpsDescription>p:first-child {
    font-size: 25px;
    height: 2%;
}
.corpsDescription>p:nth-child(2) {
    font-size: 15px;
    height: 55%;
    text-align: left;
    margin-right: 20px;
    overflow: scroll;
}
.corpsDescription>p:nth-child(2)::-webkit-scrollbar {
    width: 0px;
}
.corpsDescription>button {
    color: white;
    font-family: Cascadia Code;
    font-size: 20px;
    background-color: #292B2D;
    border: solid #363B42 2px;
    border-radius: 5px;
    width: 75%;
    height: 13%;
    cursor: pointer;
    transition: 0.3s background-color;
}
</style>