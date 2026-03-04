<script setup>
import { onMounted } from 'vue';
import HeaderComponent from '../components/HeaderComponent.vue';
import { useCustomerStore } from '../stores/customer';
import CustomerCard from '../components/CustomerCard.vue';


const customerStore = useCustomerStore();

onMounted(async () => {
    await customerStore.getCustomers();
    console.log("Dades rebudes:", customerStore.customers);
});

</script>

<template>
    <HeaderComponent />
    <section id="customers-page">
        <h2>Customer page</h2>
        <h3 v-if="customerStore.loading">Carregant...</h3>
        <h3 v-else-if="customerStore.error">Alguna cosa ha fallat</h3>
        <ul v-else class="customer-list">
            <li v-for="customer in customerStore.customers" :key="customer.id">
                <CustomerCard :customer="customer" />                
            </li>
        </ul>
    </section>

</template>

<style scoped>
.customer-list {
    list-style: none;     /* Treu els punts del <li> */
    padding: 0;
    display: grid;        /* Activa la graella */
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); 
    gap: 1.5rem;          /* Espai entre cards */
}

#customers-page {
    padding: 1rem;
}
</style>