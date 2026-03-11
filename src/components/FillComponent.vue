<script setup>
import { defineEmits, ref } from 'vue';

const emit = defineEmits(["login"]);

const userName = ref("Pedro");
const login = () => {
    emit("login", userName.value);
}
</script>

<template>
    <div class="fill">
        <slot name="top"></slot>
        <h2>Component fill</h2>
         <p>Nom d'usuari: {{ userName }}</p>
        <button @click="login">Login</button>
        <slot name="bottom"></slot>      
    </div>
</template>

<style scoped>
.fill {
    border: 3px solid gray;
}
</style>