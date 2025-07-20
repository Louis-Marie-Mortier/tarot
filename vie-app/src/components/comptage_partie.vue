<script setup>
import { ref } from 'vue';

const possible_players=ref(["A","B","C","D","E"])
const players=ref([])
const taker=ref("")
const called=ref("")
const contract=ref(0)
const poignee=ref(0)
const petit=ref(0)
const bouts=ref(0)
const score=ref(0)
const calcul=()=>{
    console.log(JSON.parse(localStorage.getItem("test"))+5)
    localStorage.setItem("test",JSON.stringify(poignee.value))
    console.log(JSON.parse(localStorage.getItem("test"))+5)
}
</script>

<template>
    <form>
        <label v-for="player in possible_players">
            <input type="checkbox" v-model="players" name="play" :value="player" :id="player+' plays'"/>
            {{ player }}
        </label>
        <label v-for="player in possible_players" v-show="players.includes(player)">
            <input type="radio" v-model="taker" name="taking" :value="player" :id="player+' takes'"/>
            {{ player }}
        </label>
        <label v-for="player in possible_players" v-show="players.length>=5 && players.includes(player)">
            <input type="radio" v-model="called" name="called" :value="player" :id="player+' called'"/>
            {{ player }}
        </label>
        <label>
            petite
            <input type="radio" v-model="contract" name="contract" value="1" id="petite"/>
        </label>
        <label>
            <input type="radio" v-model="contract" name="contract" value="2" id="garde"/>
            garde
        </label>
        <label>
            garde sans (le chien)
            <input type="radio" v-model="contract" name="contract" value="4" id="sans"/>
        </label>
        <label>
            <input type="radio" v-model="contract" name="contract" value="6" id="contre"/>
            garde contre (le chien)
        </label>
        <label>
            <input type="radio" v-model="poignee" name="poignee" value="0" id="not_enough"/>
            non annoncée
        </label>
        <label>
            <input type="radio" v-model="poignee" name="poignee" value="20" id="simple"/>
            simple ( cartes)
        </label>
        <label>
            <input type="radio" v-model="poignee" name="poignee" value="30" id="double"/>
            double ( cartes)
        </label>
        <label>
            <input type="radio" v-model="poignee" name="poignee" value="40" id="triple"/>
            triple ( cartes)
        </label>
        <label>
            <input type="checkbox" v-model="petit" name="mene au bout" value="-10" id="defense"/>
            par la défense
        </label>
        <label>
            <input type="checkbox" v-model="petit" name="mene au bout" value="0" id="aucune"/>
            aucunement
        </label>
        <label>
            <input type="checkbox" v-model="petit" name="mene au bout" value="10" id="attaque"/>
            par l'attaque
        </label>
        
        <label>
            <input type="checkbox" v-model="counted_team" name="counted" id="defenders_point"/>
            points de défense
        </label>
        <label>
            <input type="checkbox" v-model="counted_team" name="counted" id="attackants_point"/>
            points d"attaque
        </label>
        nombre de bouts de l'équipe comptée
        <label>
            <input type="radio" v-model="bouts" name="bouts" value="56" id="zero"/>
            0
        </label>
        <label>
            <input type="radio" v-model="bouts" name="bouts" value="51" id="one"/>
            1
        </label>
        <label>
            <input type="radio" v-model="bouts" name="bouts" value="41" id="two"/>
            2
        </label>
        <label>
            <input type="radio" v-model="bouts" name="bouts" value="36" id="three"/>
            3
        </label>

        <input type="number" v-model="score" name="score"/>
        {{ (counted_team?1:-1)*(score-(counted_team?bouts:91-bouts)) }}
        {{ (25*(score>=0?1:-1)+score+petit)*contract+poignee*(score>=0?1:-1) }}
        <input type="submit" value="calcul">
        <button type="button" @click="calcul">calculer</button>
    </form>
</template>