<template>
    <div class="techno"
        @mouseover="setMouseOverTete"
        @mouseout="setMouseOutTete">
        <div class="enTeteTechno"
        :style="styleTete">
            <img :src="getImageUrl(techno.image)">
            <p> {{ techno.nom }} </p>
        </div>
        <div class="corpsTechno">
            <p> {{ techno.description }} </p>
            <button
                @mouseover="setMouseOver"
                @mouseout="setMouseOut"
                @click="setMouseClick"
                :style="buttonDecouvrir"> 
            Découvrir </button>
        </div>
    </div>
</template>

<script setup>
import { reactive, ref } from 'vue';

const props = defineProps(["data"]); 
const techno = ref(null); 
techno.value = props.data; 

const buttonDecouvrir = reactive({});
const styleTete = reactive({}); 

function setMouseOver() {
    buttonDecouvrir.backgroundColor = "#222529";
}
function setMouseOut() {
    buttonDecouvrir.backgroundColor = "#292B2D";
}
function setMouseClick() {
    window.open(techno.value.lien)
}

function setMouseOverTete() {
    styleTete.backgroundColor = "#222529";
}
function setMouseOutTete() {
    styleTete.backgroundColor = "#292B2D";
}

function getImageUrl(image) {
  return new URL(`../assets/img/techno/${image}`, import.meta.url).href;
}
</script>

<style>
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
    margin-top: 1vw;
}
.enTeteTechno {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #292B2D;
    transition: 0.3s background-color;
}
.corpsTechno {
    height: 100%;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #262626;
    border-top: solid #363B42 3px;
    box-sizing: border-box;
}
.corpsTechno>p {
    width: 90%;
    height: 50%;
    text-align: center;
    font-size: 17px;
    overflow: scroll;
    margin-bottom: 0;
}
.corpsTechno>p::-webkit-scrollbar {
    width: 0px;
}
.corpsTechno>button {
    height: auto;
    width: 60%;
    color: white;
    font-family: Cascadia Code;
    background-color: #292B2D;
    border: solid #363B42 2px;
    border-radius: 5px;
    font-size: 15px;
    padding-block: 10px;
    transition: 0.3s background-color;
    cursor: pointer;
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

@media  screen and (max-width: 800px) {
    .techno {
        min-width: 0;
        min-height: 0;
        width: 45vw;
        height: 30vw;
        display: grid;
        grid-template: 30% 70% / 1fr;
        border-radius: 5px;
        border: solid #363B42 2px;
        box-sizing: border-box;
        overflow: hidden;
    }
    .enTeteTechno>p {
        font-size: 4vw;
    }
    .corpsTechno>button {
        height: auto;
        width: 60%;
        color: white;
        font-family: Cascadia Code;
        background-color: #292B2D;
        border: solid #363B42 2px;
        border-radius: 5px;
        font-size: 2.5vw;
        padding-block: 3px;
        transition: 0.3s background-color;
        cursor: pointer;
    }
    .corpsTechno {
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: #262626;
        border-top: solid #363B42 2px;
        box-sizing: border-box;
    }
    .corpsTechno>p {
        width: 90%;
        height: 50%;
        text-align: center;
        font-size: 2.2vw;
        overflow: scroll;
        margin-bottom: 0;
    }
    .enTeteTechno>img {
        max-width: 80%;
        max-height: 80%;
        height: auto;
        width: auto;
        padding-right: 2vw;
    }
}

@media (max-width: 1600px) and (min-width: 500px) {
    .techno {
        min-width: 0;
        min-height: 0;
        width: 270px;
        height: 180px;
        display: grid;
        grid-template: 30% 70% / 1fr;
        border-radius: 5px;
        border: solid #363B42 3px;
        box-sizing: border-box;
        overflow: hidden;
    }
    .enTeteTechno>p {
        font-size: 25px;
    }
    .corpsTechno>button {
        height: auto;
        width: 60%;
        color: white;
        font-family: Cascadia Code;
        background-color: #292B2D;
        border: solid #363B42 3px;
        border-radius: 5px;
        font-size: 15px;
        padding-block: 3px;
        transition: 0.3s background-color;
        cursor: pointer;
    }
    .corpsTechno {
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: #262626;
        border-top: solid #363B42 3px;
        box-sizing: border-box;
    }
    .corpsTechno>p {
        width: 90%;
        height: 50%;
        text-align: center;
        font-size: 13px;
        overflow: scroll;
        margin-bottom: 0;
    }
    .enTeteTechno>img {
        max-width: 80%;
        max-height: 80%;
        height: auto;
        width: auto;
        padding-right: 10px;
    }
}
</style>

