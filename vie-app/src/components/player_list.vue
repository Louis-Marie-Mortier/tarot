<script setup>
import { ref } from 'vue';


const players =  ref(["rrvr"])
const selected =  ref([])
const new_player = ref("")
localStorage
IDBOpenDBRequest
indexedDB
const add_player = ()=>{
    console.log("ajout du joueur ${new_player}");
    players.value=players.value.concat(new_player.value);
    new_player.value='';
}
</script>

<template>
    <div>
        <input v-model="new_player"/>
        <input type="button" value="add_np" @click="add_player"/>
        <p>
            {{ players }}
        </p>
    </div>
    <div>
        <select v-model="selected" multiple>
        <option v-for="player in players">{{player}}</option>
        </select>
    </div>
</template>