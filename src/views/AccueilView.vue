<template>
    <section id="accueil">
        <div class="barreBienvenue">
            <p>Bienvenue sur mon portfolio</p>
        </div>
        <div class="barreMenu" id="barreMenu">
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
        <div class="titre" id="titreMetier">
            <p> <strong> Futur Développeur Full-Stack </strong> </p>
        </div>
        <div class="carrousel">
            <img src="../assets/img/accueil/fleche.png" id="btGauche" class="boutonFleche">
            <img src="../assets/img/accueil/fleche.png" id="btDroite" class="boutonFleche">
            <div class="containerAccueil" id="containerAccueil" :style="styleContainer">
                <img v-for="k in accueil.imageCarrousel" 
                    :src="`../assets/img/accueil/${k}`">
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
const image = ref(null); 

onMounted(() => {
    //CONFIGURATION DE LA BARRE DU MENU //
    const barreMenu = document.getElementById("barreMenu");
    function scrollFunction() {
        if (document.body.scrollTop > 50 || document.documentElement.scrollTop > 50) {
            barreMenu.style.position = "fixed";
            barreMenu.style.top = "0";
            barreMenu.style.backgroundColor = "black";
        } else {
            barreMenu.style.position = "absolute";
            barreMenu.style.top = "unset";
            barreMenu.style.backgroundColor = "transparent";
        }
    }

    function setActionScrollingBarreMenu() {
        window.onscroll = function () { scrollFunction() };
    }
    //FIN DE LA CONFIGURATION DE LA BARRE DU MENU //

    //CONFIGURATION DU CAROUSSEL//
    const container = document.getElementById("containerAccueil");
    var tailleImage = container.offsetWidth;

    var indice = 0;
    var droite = true;
    var gauche = false;
    var timerCarroussel;
    const nbImage = accueil.value.imageCarrousel.length; 
    const btFlecheDroite = document.getElementById("btDroite");
    const btFlecheGauche = document.getElementById("btGauche");

    const btFleche = document.querySelectorAll(".boutonFleche");

    function setActionBtFlecheAccueil() {
        btFleche.forEach(function (bt) {
            bt.addEventListener("mouseover", function () {
                bt.style.opacity = "100%";
            });
            bt.addEventListener("mouseout", function () {
                bt.style.opacity = "30%";
            })
        });
        btFlecheDroite.addEventListener("click", function () {
            if (indice < nbImage - 1) {
                indice++;
                defilementCarroussel();
                stopTimerCarroussel();
                startTimerCarroussel();
                if (indice == nbImage - 1) {
                    droite = false;
                    gauche = true;
                }
            }
        });
        btFlecheGauche.addEventListener("click", function () {
            if (indice > 0) {
                indice--;
                defilementCarroussel();
                stopTimerCarroussel();
                startTimerCarroussel()
                if (indice == 0) {
                    droite = true;
                    gauche = false;
                }
            }
        });
        window.addEventListener("resize", function () {
            tailleImage = container.offsetWidth;
            defilementCarroussel();
            stopTimerCarroussel();
            startTimerCarroussel();
        });
    }

    function defilementCarroussel() {
        container.style.transform = "translateX(" + -(indice * tailleImage) + "px)";
    }
    function startTimerCarroussel() {
        timerCarroussel = setInterval(function () {
            if (droite) {
                indice++;
                if (indice == nbImage - 1) {
                    droite = false;
                    gauche = true;
                }
            } else if (gauche) {
                indice--;
                if (indice == 0) {
                    droite = true;
                    gauche = false;
                }
            }
            defilementCarroussel();
        }, 4000);
    }
    function stopTimerCarroussel() {
        clearInterval(timerCarroussel);
    }
    //FIN DE LA CONFIGURATION DU CAROUSSEL//
    const btMenu = document.querySelectorAll(".btMenu strong p a");
    function setActionBtMenu() {
        btMenu.forEach(function (bt) {
            bt.addEventListener("mouseover", function () {
                bt.style.textDecoration = "underline";
                bt.style.color = "rgb(213, 213, 213)";
            });
            bt.addEventListener("mouseout", function () {
                bt.style.textDecoration = "none";
                bt.style.color = "white";
            });
        });
    }

    const titre = document.getElementById("titreMetier");
    titre.addEventListener("mouseover", function () {
        titre.style.color = "black";
        titre.style.backgroundColor = "white";
    });
    titre.addEventListener("mouseout", function () {
        titre.style.color = "white";
        titre.style.backgroundColor = "transparent";
    });

    setActionScrollingBarreMenu(); 
    setActionBtMenu();  
    setActionBtFlecheAccueil(); 
    startTimerCarroussel(); 
});
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
}

#btDroite {
    right: 0;
    transform: rotate(180deg);
    margin-right: 20px;
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
</style>