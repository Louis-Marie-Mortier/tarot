<script setup>
import { ref } from 'vue';
const scores=ref({"A":[1,2,3],"B":[4,5,6]});
</script>

<template>
    <table>
        <thead>
            <th v-for="player in Object.keys(scores)">{{ player }}</th>
        </thead>
        <tbody>
            <tr v-for="partie in Object.values(scores).at(0).length">
                <td v-for="player in Object.keys(scores)">
                    {{ scores[player].at(partie) }}
                </td>
            </tr>
        </tbody>
    </table>
</template>