<script setup>
import HeaderComponent from '../components/HeaderComponent.vue';
import { ref } from 'vue';
import { computed } from 'vue';
const myId = "unAltreId";
const myCondition = false;

const myValue = ref("unaltrenom");
const longitud = computed(() => {
    return myValue.value.length
});

const fruites = ["poma","pera","pruna"];


</script>

<template>
    <HeaderComponent />
    <h2>Home page</h2>

    <h3 :class="myCondition ? 'clar':'fosc'" :id="myId">Exemple v-bind</h3>
    <h3 :class="{clar: myCondition, fosc: true}" >Exemple v-bind</h3>

    <p>{{ myValue }}</p>
    <p>longitud del nom: {{ longitud }}</p>
    <input type="text" v-model="myValue" />

    <ul>
        <li v-for="(fruit, index) in fruites" :key="index">
            {{ index  + 1}} - {{ fruit }}
        </li>
    </ul>

</template>

<style scoped>
.clar {
    background-color: bisque;
    color: red;
}
.fosc {
    background-color: brown;

}
</style>