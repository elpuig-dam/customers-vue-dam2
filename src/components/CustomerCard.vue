<script setup>

const props = defineProps( {
  customer: {
    type: Object,
    required: true
  }
});

</script>

<template>
    <div v-if="props.customer">
        <div class="avatar">
          {{ props.customer.firstName?.charAt(0) }}{{ props.customer.lastName?.charAt(0) }}
        </div>
        {{ props.customer.firstName }} {{ props.customer.lastName }}
        <span class="value">{{ props.customer.email }}</span>
        <p class="label">Incidències</p>
        <span :class="['status-tag', props.customer.incidencies?.length > 0 ? 'active' : 'empty']">
          {{ props.customer.incidencies?.length || 0 }} assignades
        </span>
        <div class="card-footer">
          <router-link :to="{name: 'customer-detail', params: {id: customer.id}}">
            <button>Veure detalls</button>
          </router-link>
          
        </div>
    </div>
 
</template>

<style scoped>

.avatar {
  width: 48px;
  height: 48px;
  background-color: #4f46e5; /* Color lila/blau modern */
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 1.2rem;
}


.label {
  font-size: 0.9rem;
  letter-spacing: 0.15rem;
  color: #9ca3af;
}

.value {
  font-size: 0.95rem;
  color: #374151;
}

.status-tag {
  display: inline-block;
  font-size: 0.85rem;
  margin-top: 4px;
}

.status-tag.active { color: #059669; font-weight: 500; }
.status-tag.empty { color: #9ca3af; }


</style>