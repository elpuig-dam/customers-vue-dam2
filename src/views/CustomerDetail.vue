<script setup>
import { useRoute } from 'vue-router';
import HeaderComponent from '../components/HeaderComponent.vue';
import { onMounted, ref } from 'vue';
import { useCustomerStore } from '../stores/customer';


const route = useRoute();
const customer = ref(null);

const customerStore = useCustomerStore();

onMounted( async () => {
    const id = route.params.id;
    console.log("id del customer",id);
    //customer.value = await customerStore.getCustomerById(id);
    customer.value = customerStore.customers.find(c => c.id == id);
});

</script>

<template>
    <HeaderComponent></HeaderComponent>
    <div v-if="customer" class="detail-customer">
        <h1>Detalls de {{ customer.firstName }}</h1>
        <p><strong>ID:</strong>{{ customer.id }}</p>
        <p><strong>EMAIL:</strong>{{ customer.email }}</p>
        <hr>
        <h3>Incidències</h3>
        <ul>
            <li v-for="inc in customer.incidencies" :key="inc.id">
                {{ inc.titol }} - {{ inc.estat }}
            </li>
        </ul>
    </div>


</template>