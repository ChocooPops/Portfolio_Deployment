<template>
<section id="profil">
        <div class="profil">
            <p class="titreSection"> <strong>Mon profil</strong></p>
            <p class="sousTitre"> A propos de mes <a class="noir">passions :</a></p>
            <p class="texteProfil"> La programmation est plus qu’une compétence professionnelle, c’est un moyen
                d’expression et d’innovation qui me passionne profondément. Elle m’offre la liberté de créer et de
                résoudre
                des problèmes uniques, transformant des idées abstraites en réalité tangibles. La programmation n’a
                aucune
                limite, hormis celle du développeur. C’est pourquoi je suis quotidiennement à la recherche de maîtrise
                de nouvelles technologies qui me permettront d’atteindre le plus haut sommet de réalisation possible.
            </p>
            <div class="passion">
                <div class="cinema">
                    <img src="../assets/img/profil/setup.jpeg" alt="Mon Image" id="imgSetup" ref="imgSetup"
                        @mouseover="mouseOverSetup"
                        @mouseout="mouseOutSetup">
                    <div class="cinemaText">
                        <p class="sousTitre">Cinéma / <a class="noir">Photographie</a></p>
                        <p class="texteProfil">La capacité qu’a le cinéma à capturer l’imagination et à évoquer des
                            émotions profondes,
                            en fait l’une de mes passions les plus ardentes. Il est l’une des formes d’art les plus
                            maîtrisés, combinant
                            la narration, le visuel, le spectacle, et la musique, pour en engendrer des expériences
                            immersives et mémorables.
                        </p>
                    </div>
                    <img src="../assets/img/profil/MadMax.png" alt="Mon Image" id="imgMadMax" style="margin-top: 5px;" ref="imgMadMax"
                        @mouseover="mouseOverMadMax"
                        @mouseout="mouseOutMadMax">
                </div>
                <div class="jeuVidéo">
                    <p class="sousTitre">Jeux <a class="noir">Vidéo</a></p>
                    <p class="texteProfil"> Découvrir des mondes riches et immersif. Vivre des récits épiques
                        et en étant à la fois spectateur et acteur principal. </p>
                    <img src="../assets/img/profil/falcon.png" alt="Mon Image" id="imgFalcon" ref="imgFalcon"
                        @mouseover="mouseOverFalcon"
                        @mouseout="mouseOutFalcon">
                    <img src="../assets/img/profil/zelda.jpeg" alt="Mon Image" id="imgZelda" ref="imgZelda"
                        @mouseover="mouseOverZelda"
                        @mouseout="mouseOutZelda">
                </div>
            </div>
            <p class="sousTitre"> Mes <a class="noir">études</a></p>
            <p class="texteProfil"> J’ai commencé à m’intéresser à l’informatique à partir de 2021 d’un point de vue
                hardware. Au lycée La
                Martinière Monplaisir, j’avais comme mission de manipuler du matériel informatique afin de réparer
                et de
                monter de A à Z des ordinateurs.
                <br>C’est en 2022 que j’ai poursuivi mes études en BUT Informatique à Lyon 1. Je continue toujours
                ma
                formation afin d’accumuler des compétences et d’approfondir mes connaissances sur certains langages de
                programmation et de plusieurs Framework. Dès lors, je me suis engagé dans le parcours réalisation et
                développement d’applications afin de devenir un développeur Full-Stack.
            </p>
        </div>
        <div class="descriptionImg" id="description1" :style="descSetup"
            @mouseover="mouseOverSetup"
            @mouseout="mouseOutSetup">
            <p> Mon environnement de travail : <br>
                C’est sur ce bureau que j’écris chaque ligne de code comme une pièce de <br>
                puzzle à implémenter dans une de mes applications. Mon temps à faire de la <br>
                programmation s’effectue majoritairement sur ce lieu de travail, avec un Pc <br>
                doté d’un Intel Core i7 12700k, 32Go de ram, et une carte graphique AMD RX <br>
                7900XT. Le confort que m’apporte cet environnement me permet de me baigner <br>
                pleinement dans le code, tout en plongeant dans une concentration et une <br>
                immersion absolue, afin d’optimiser mon travail.
            </p>
        </div>
        <div class="descriptionImg" id="description2" :style="descMadMax"
            @mouseover="mouseOverMadMax"
            @mouseout="mouseOutMadMax">
            <p>La magie du cinéma réside dans son pouvoir à nous transporter dans le temps <br>
                et l’espace, de nous faire vivre des vies que nous n’avons jamais vécues, <br>
                enrichissant ainsi notre compréhension de l’humanité. La mise en scène <br>
                est ce qui me fascine le plus. Elle est l’élément crucial du cinéma <br>
                puisqu’elle représente l’art de raconter visuellement une histoire. <br>
                Elle orchestre avec minutie le jeu des acteurs, la composition de <br>
                chaque plan, le mouvement de la caméra et l’utilisation de la lumière <br>
                ainsi que l’éclairage. Ainsi, toute cette harmonie donne une véritable <br>
                ambiance et un ton au film. Le cinéma transforme les mots d’un scénario <br>
                en images puissantes et chargées de détails. Quant à la photographie, <br>
                elle fait vibrer ma sensibilité esthétique. Que ce soit l’utilisation de <br>
                couleur en noir et blanc pour renforcer une ambiance sinistre, ou d’une <br>
                photo éclairée de couleurs complémentaires, la photographie reflète une <br>
                vision du monde. Elle peut révéler la beauté d’un ordinaire et d’une <br>
                perspective unique, agissant comme un miroir entre le réel et le fictif.
            </p>
        </div>
        <div class="descriptionImg" id="description3" :style="descFalcon"
            @mouseover="mouseOverFalcon"
            @mouseout="mouseOutFalcon">
            <p>
                Exploration & Contemplation : <br>
                Les jeux vidéo d’exploration et de <br>
                contemplation sont un moyen <br>
                d’échappatoire merveilleux. Ils sont <br>
                une expérience méditative unique dans <br>
                laquelle l’exploration tranquille au <br>
                paysage magnifique m’inspire. La <br>
                narration subtile par l’environnement, <br>
                témoignant des pratiques d’une <br>
                civilisation par leurs vestiges, ou <br>
                d’une mythologie, me procure une <br>
                liberté d’interprétation qui satisfait <br>
                mon imagination. Le gameplay ainsi que <br>
                la liberté de se mouvoir dans un monde <br>
                doté d’un gigantisme architectural <br>
                complexe qui nous écrase, m’offre un <br>
                vent de liberté et une joie de me <br>
                perdre dans un monde onirique.
            </p>
        </div>
        <div class="descriptionImg" id="description4" :style="descZelda"
            @mouseover="mouseOverZelda"
            @mouseout="mouseOutZelda">
            <p> Je suis aussi à la recherche de nervosité, <br>
                de dynamisme, ainsi qu’un état de <br>
                concentration absolue, qui se reflètent <br>
                dans les jeux de combat. La maîtrise <br>
                technique et d’exécution sont quelque chose <br>
                que je convoite, sans oublier la nécessité <br>
                d’avoir de grands réflexes. La compétition <br>
                me force également à donner le meilleur de <br>
                moi-même, dans une danse complexe où la <br>
                vitesse, la précision et l’adaptation <br>
                déterminent le vainqueur. </p>
        </div>
    </section>
</template>

<script setup>
import { onMounted, reactive, ref } from 'vue';

const imgSetup = ref(null);
const imgFalcon = ref(null); 
const imgZelda = ref(null); 
const imgMadMax = ref(null); 

const descSetup = reactive({}); 
const descFalcon = reactive({});
const descZelda = reactive({}); 
const descMadMax = reactive({}); 

function updateSizes() {
    descSetup.height = imgSetup.value.clientHeight + "px"; 
    descMadMax.height = imgMadMax.value.clientHeight + "px";
    descFalcon.width = imgFalcon.value.clientWidth + "px"; 
    descZelda.width = imgZelda.value.clientWidth + "px"; 
};

setTimeout(function() {
    updateSizes(); 
}, 1); 

onMounted(function() {
    updateSizes(); 
    window.addEventListener('resize', updateSizes);
})

function setOut(style, type) {
    if (type) {
        style.width = "0"; 
    } else {
        style.height = "0"; 
    }
}

function setOver(style, ref, type) { 
    style.left = ref.value.offsetLeft + "px"; 
    style.top = ref.value.offsetTop + "px"; 
    if (type) {
        style.width = ref.value.clientWidth + "px"
        style.height = ref.value.clientHeight + "px"; 
    } else {
        style.height = ref.value.clientHeight + "px"
        style.width = ref.value.clientWidth + "px"
    }
}

function mouseOverSetup() {
    setOver(descSetup, imgSetup, true); 
}
function mouseOutSetup() {
    setOut(descSetup, true); 
}

function mouseOverMadMax() {
    setOver(descMadMax, imgMadMax, true); 
}
function mouseOutMadMax() {
    setOut(descMadMax, true); 
}

function mouseOverFalcon() {
    setOver(descFalcon, imgFalcon, false); 
}
function mouseOutFalcon() {
    setOut(descFalcon, false); 
}

function mouseOverZelda() {
    setOver(descZelda, imgZelda, false); 
}
function mouseOutZelda() {
    setOut(descZelda, false); 
}

</script>

<style>
/*
//////////////////////////////////////////////////////////////////////////// PROFIL //////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////// PROFIL //////////////////////////////////////////////////////////////////////////  
////////////////////////////////////////////////////////////////////////// PROFIL //////////////////////////////////////////////////////////////////////////
*/

#profil {
    height: auto;
    width: auto;
    background-color: #303030;
    overflow: hidden;
}

.profil {
    height: auto;
    width: auto;
    margin-left: 5vw;
    margin-right: 5vw;
}
.profil>p:first-child {
    margin-top: 8vw;
}
.titreSection {
    text-align: center;
    font-size: 3vw;
}

.sousTitre {
    text-align: center;
    font-size: 2.3vw;
}

.texteProfil {
    font-size: 1.4vw;
    text-align: center;
    justify-content: center;
    word-wrap: break-word;
    overflow-wrap: break-word;
    margin-bottom: 2vw;
}

.passion {
    display: grid;
    grid-template: auto / 65% 35%;
    grid-column-gap: 2vw;
}

.jeuVidéo {
    display: flex;
    flex-direction: column;
    flex-wrap: 10px;
    justify-items: center;
    text-align: center;
}

.jeuVidéo>p:nth-child(1) {
    margin-top: 0;
    margin-bottom: 1px;
    padding-top: 0;
}

.jeuVidéo>img {
    cursor: pointer;
}

.jeuVidéo>img:first-child {
    height: 100%;
    width: 100%;
    border-radius: 2vw;
    object-fit: cover;
}

.jeuVidéo>img:last-child {
    margin-top: 2vw;
    height: 100%;
    width: 100%;
    border-radius: 2vw;
    object-fit: cover;
}

.cinema {
    display: grid;
    grid-template: 40% 20% 40% / 100%;
}

.cinema>img {
    height: 100%;
    width: 100%;
    border-radius: 2vw;
    object-fit: cover;
    cursor: pointer;
}

.cinemaText {
    display: flex;
    flex-direction: column;
    text-align: center;
    justify-content: center;
}

.cinemaText>p:last-child {
    margin-top: -0.5vw;
}

.noir {
    color: black;
}

.profil> :last-child {
    margin-inline: 20%;
    margin-bottom: 0;
}

.descriptionImg {
    height: 0;
    width: 0;
    position: absolute;
    opacity: 70%;
    background-color: #000000;
    transition: 0.5s height, 0.5s width;
    border-radius: 2vw;
    cursor: pointer;
    overflow: hidden;
    white-space: nowrap;
}

.descriptionImg>p {
    position: absolute;
    text-align: center;
    justify-content: center;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 1.2vw;
}

.degrade {
    width: 100%;
    height: 8vw;
    background: linear-gradient(180deg, #303030, #262626);
    margin: 0;
    padding: 0;
}
</style>