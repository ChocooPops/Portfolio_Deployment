<template>
    <section id="accueil">
        <div class="barreBienvenue">
            <p>Bienvenue sur mon portfolio</p>
        </div>
        <div class="barreMenu" id="barreMenu" :style="barreMenu">
            <p class="nom"> Nahil </p>
            <div class="btMenu">
                <strong>
                    <p> <a href="#accueil">Accueil</a></p>
                </strong>
                <strong>
                    <p> <a href="#profil">Profil</a></p>
                </strong>
                <strong>
                    <p> <a href="#technologies">Technologies</a></p>
                </strong>
                <strong>
                    <p> <a href="#projets">Projets</a></p>
                </strong>
                <strong>
                    <p> <a href="#competences">Compétences</a></p>
                </strong>
            </div>
        </div>
        <div class="titre" id="titreMetier" 
            @mouseover="mouseOverMetier"
            @mouseout="mouseOutMetier"
            :style="titreMetier">
            <p> <strong> Futur Développeur Full-Stack </strong> </p>
        </div>
        <div class="carrousel">
            <img src="../assets/img/accueil/fleche.png" id="btGauche" class="boutonFleche"
                @click="clickBtGauche"
                @mouseover="mouseOverBtGauche"
                @mouseout="mouseOutBtGauche"
                :style="btGauche">
            <img src="../assets/img/accueil/fleche.png" id="btDroite" class="boutonFleche"
                @click="clickBtDroite"
                @mouseover="mouseOverBtDroite"
                @mouseout="mouseOutBtDroite"
                :style="btDroite">
            <div class="containerAccueil" id="containerAccueil" :style="styleContainer">
                <img v-for="image in accueil.imageCarrousel" :src="getImageUrl(image)" :key="image" ref="imgCarrousel">
            </div>
        </div>
    </section>
</template>

<script setup>
import { onMounted, reactive, ref} from 'vue';

const props = defineProps(["data"]); 
const accueil = ref(null);
accueil.value = props.data.Accueil;
const styleContainer = reactive({});
styleContainer.gridTemplate = "100% / repeat(" + accueil.value.imageCarrousel.length + ", 100%)"; 

function getImageUrl(image) {
  return new URL(`../assets/img/accueil/${image}`, import.meta.url).href;
}

// ACTION DE LA BARRE DU MENU AVEC DEFILEMENT DU SCROLLING
const body = document.body; 
const barreMenu = reactive({});
function scrollFunction() {
    if (body.scrollTop > 50 || document.documentElement.scrollTop > 50) {
        barreMenu.position = "fixed";
        barreMenu.top = "0";
        barreMenu.backgroundColor = "black";
    } else {
        barreMenu.position = "absolute";
        barreMenu.top = "unset";
        barreMenu.backgroundColor = "transparent";
    }
}

    //MISE EN PLACE DU CARROUSEL
const imgCarrousel = ref(null); 
let indice = 0;
let droite = true;
let gauche = false;
const nbImage = accueil.value.imageCarrousel.length; 

function defilementCarrousel() {
    var tailleImage = imgCarrousel.value[0].clientWidth; 
    styleContainer.transform = "translateX(" + -(indice * tailleImage) + "px)";
}

    //STYLE ET ACTION DU BOUTON DROITE DU CARROUSEL
const btDroite = reactive({});
function clickBtDroite() {
    if (indice < nbImage - 1) {
        indice ++; 
        stopTimerCarrousel(); 
        startTimerCarrousel(); 
        defilementCarrousel(); 
        if (indice == nbImage - 1) {
            droite = false;
            gauche = true;
        }
    }
}

function mouseOverBtDroite() {
    btDroite.opacity = "100%"; 
}
function mouseOutBtDroite() {
    btDroite.opacity = "30%"; 
}

    //STYLE ET ACTION DU BOUTON DROITE DU CARROUSEL
const btGauche = reactive({});
function clickBtGauche() {
    if (indice > 0) {
        stopTimerCarrousel(); 
        startTimerCarrousel(); 
        indice--;
        defilementCarrousel();
        if (indice == 0) {
            droite = true;
            gauche = false;
        }
    }
}
function mouseOverBtGauche() {
    btGauche.opacity = "100%"; 
}
function mouseOutBtGauche() {
    btGauche.opacity = "30%"; 
}

    //STYLE DU TITRE METIER; 
const titreMetier = reactive({}); 
function mouseOutMetier() {
    titreMetier.color = "white";
    titreMetier.backgroundColor = "transparent";  
}
function mouseOverMetier() {
    titreMetier.color = "black"; 
    titreMetier.backgroundColor = "white"; 
}

onMounted(() => {
    window.onscroll = function () { scrollFunction() };
    window.addEventListener("resize", defilementCarrousel); 
});

let timerCarrousel;
function startTimerCarrousel() {
    timerCarrousel = setInterval(function(){
        if(droite) {
            indice ++; 
            defilementCarrousel(); 
            if (indice == nbImage - 1) {
                droite = false;
                gauche = true;
            }
        } else if (gauche) {
            indice --; 
            defilementCarrousel(); 
            if (indice == 0) {
                droite = true;
                gauche = false;
            }
        }
    }, 3000)
}

function stopTimerCarrousel() {
    clearInterval(timerCarrousel); 
}
startTimerCarrousel(); 
</script>

<style>
#accueil {
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
    position: relative;
    overflow: hidden;
}

.barreBienvenue {
    width: 100%;
    height: auto;
    background-color: black;
    margin: 0;
}

.barreBienvenue>p {
    color: white;
    text-align: center;
    font-size: 1.2vw;
    padding: 0.7vw;
    font-family: Cascadia Code;
    margin: 0;
}

.barreMenu {
    width: 100%;
    height: auto;
    background-color: transparent;
    margin: 0;
    color: white;
    display: flex;
    align-items: center;
    position: absolute;
    transition: 0.7s background-color;
    z-index: 3;
}

.btMenu {
    position: absolute;
    width: 100%;
    display: flex;
    justify-content: center;
}

.btMenu>strong>p {
    font-family: Cascadia Code;
    font-size: 1.8vw;
    font-style: bold;
    padding-inline: 1.5vw;
    cursor: pointer;
    transition: 0.3s color;
}

.nom {
    text-align: left;
    font-family: Amplify;
    font-size: 4.8vw;
    margin: 6px;
    padding-left: 2vw;
}

.titre {
    height: auto;
    width: auto;
    background-color: transparent;
    border: white solid 3px;
    color: white;
    font-family: Cascadia Code;
    bottom: 0;
    right: 0;
    position: absolute;
    border-radius: 60px;
    display: flex;
    justify-content: center;
    margin-bottom: 3%;
    margin-right: 4%;
    z-index: 2;
    transition: 0.3s color, 0.3s background-color linear;
    cursor: pointer;
}

.titre>p {
    text-align: center;
    font-size: 2vw;
    margin: 0;
    padding-inline: 2.5vw;
    padding-block: 0.8vw;
}

.carrousel {
    height: 100%;
    width: 100%;
    margin: 0;
    padding: 0;
    position: relative;
    z-index: 0;
}

.carrousel>img {
    position: absolute;
    top: 50%;
    opacity: 30%;
    transition: 0.3s opacity;
    cursor: pointer;
    z-index: 2;
}

#btGauche {
    left: 0;
    margin-left: 20px;
    height: 3.5vw;
    width: 3.5vw;;
}

#btDroite {
    right: 0;
    transform: rotate(180deg);
    margin-right: 20px;
    height: 3.5vw;
    width: 3.5vw;
}

.containerAccueil {
    height: 100%;
    width: 100%;
    margin: 0;
    padding: 0;
    display: grid;
    grid-template: 100% / repeat(7, 100%);
    transition: all 0.5s ease;
}

.containerAccueil>img {
    height: 100%;
    width: 100%;
    object-fit: cover;
}

.btMenu > strong > p > a:hover {
    text-decoration: underline;
    color:rgb(213, 213, 213);
}

@media  screen and (max-width: 700px) {
    #btGauche {
        left: 0;
        margin-left: 20px;
        height: 30px;
        width: 30px;
    }
    #btDroite {
        right: 0;
        transform: rotate(180deg);
        margin-right: 20px;
        height: 30px;
        width: 30px;
    }
    .titre {
        height: auto;
        width: auto;
        background-color: transparent;
        border: white solid 3px;
        color: white;
        font-family: Cascadia Code;
        bottom: 0;
        right: 0;
        position: absolute;
        border-radius: 60px;
        display: flex;
        justify-content: center;
        margin-bottom: 7%;
        margin-right: 4%;
        z-index: 2;
        transition: 0.3s color, 0.3s background-color linear;
        cursor: pointer;
    }
    .titre>p {
        text-align: center;
        font-size: 4.2vw;
        margin: 0;
        padding-inline: 5vw;
        padding-block: 1.8vw;
    }
    .barreBienvenue>p {
        color: white;
        text-align: center;
        font-size: 2.5vw;
        padding: 1.2vw;
        font-family: Cascadia Code;
    }
    
    .barreMenu {
        width: 100%;
        height: auto;
        background-color: transparent;
        margin: 0;
        color: white;
        display: flex;
        align-items: center;
        position: absolute;
        transition: 0.7s background-color;
        z-index: 3;
    }

    .nom {
        position: relative;
        left: 50%;
        transform: translate(-50%);
        font-family: Amplify;
        font-size: 8vw;
    }

    .btMenu {
        display: none
    }

}

</style>