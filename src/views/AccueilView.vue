<template>
    <section id="accueil">
        <div class="barreBienvenue">
            <p> Bienvenue sur mon portfolio </p>
        </div>
        <div class="barreMenu" id="barreMenu" :style="barreMenu">
            <p class="nom" :style="nomStyle"> Nahil </p>
            <div class="btBurger"
                @click="clickBtBurger"
                @mouseover="mouseOverBurger"
                @mouseout="mouseOutBurger"
                :style="btBurger">
                <div class="barreBurger" :style="barreBurger1" ref="refBarre1"> </div>
                <div class="barreBurger" :style="barreBurger2" ref="refBarre2"> </div>
                <div class="barreBurger" :style="barreBurger3" ref="refBarre3"> </div>
            </div>
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
        <div class="menuBurger" :style="menuBurger" ref="menuBurgerTaille">
            <div class="sectionBurger">
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

//MENU BURGER POUR TELEPHONE; 
const menuBurger = reactive({}); 
const nomStyle = reactive({}); 
const menuBurgerTaille = ref(null); 
const barreBurger1 = reactive({}); 
const barreBurger2 = reactive({}); 
const barreBurger3 = reactive({}); 
const btBurger = reactive({}); 


function clickBtBurger() {
    if (menuBurgerTaille.value.clientWidth <=0 ) {
        nomStyle.opacity = "0"; 
        menuBurger.width = "56.5%"; 
        barreBurger1.position = "absolute";
        barreBurger2.position = "absolute";
        barreBurger3.position = "absolute"; 
        btBurger.left = "85%";
        btBurger.transform = "translate(-85%)";
        barreBurger1.transform = "rotate(45deg)";
        barreBurger2.opacity = "0"
        barreBurger3.transform = "rotate(135deg)";
    } else {
        nomStyle.opacity = "1"; 
        menuBurger.width = "0"; 
        barreBurger1.position = "relative";
        barreBurger2.position = "relative";
        barreBurger3.position = "relative";
        barreBurger1.transform = "rotate(180deg)";
        barreBurger2.opacity= "1"
        barreBurger3.transform = "rotate(0deg)";
        btBurger.left = "90%";
        btBurger.transform = "translate(-90%)";
    }
}
function mouseOverBurger() {

}
function mouseOutBurger() {

}
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
    z-index: 4;
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

.btBurger {
    display: none;
}

@media  screen and (max-width: 800px) {
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
        border: white solid 2px;
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

    .nom {
        position: relative;
        left: 50%;
        transform: translate(-50%);
        font-family: Amplify;
        font-size: 8.5vw;
        transition: 0.3s opacity;
    }

    .btMenu {
        display: none
    }

    .btBurger {
        display: block;
        position: absolute; 
        left: 90%;
        transform: translate(-90%);
        font-family: Amplify;
        font-size: 8vw;
    }

    .barreBurger {
        width: 6vw;
        height: 1vw;
        border-radius: 2vw;
        margin-bottom: 0.5vw;
        background-color: white;
        transition: 0.5s all ease;
    }

    .btBurger > .barreBurger:first-child  {
        transform: rotate(180deg)
    }

    .menuBurger {
        transition: 0.5s width;
        right: 0;
        top: 0; 
        position: fixed;
        height: 100%;
        width: 0;
        background: black;
        z-index: 3;
    }

    .sectionBurger {
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
        margin-top: 14vw;
        font-size: 4.2vw;
    }

    .sectionBurger > strong > p > a {
        margin-left: 15%;
    }

    .sectionBurger > strong > p > a:hover {
        text-decoration: underline;
        color:rgb(213, 213, 213);
    }
}

</style>