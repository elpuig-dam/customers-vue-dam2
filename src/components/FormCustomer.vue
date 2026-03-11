<script setup>
import { useCustomerStore } from '../stores/customer';
import { ref } from 'vue';

// Objecte inicial buit
const newCustomer = ref({
    firstName: '',
    lastName: '',
    email: '',
    incidencies: []
});

const customerStore = useCustomerStore();

const handleSubmit = async () => {
    await customerStore.addCustomer(newCustomer.value);
    //console.log(newCustomer);
    newCustomer.value = { 
        firstName: '', 
        lastName: '', 
        email: '', 
        incidencies: [] 
    };
}

</script>

<template>
     <form @submit.prevent="handleSubmit" class="add-form">
        <input v-model="newCustomer.firstName" placeholder="Nom" required>
        <input v-model="newCustomer.lastName" placeholder="Cognom" required>
        <input v-model="newCustomer.email" type="email" placeholder="Email" required>
        <button type="submit">Afegir</button>
    </form>

</template>

<style scoped>
</style>