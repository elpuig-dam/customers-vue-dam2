<script setup>

const props = defineProps( {
  customer: {
    type: Object,
    required: true
  }
});

</script>

<template>
    
        <div class="avatar">
          {{ props.customer.firstName.charAt(0) }}{{ props.customer.lastName.charAt(0) }}
        </div>
        <div class="header-info">
          <h3>{{ props.customer.firstName }} {{ props.customer.lastName }}</h3>
        </div>
    
    
      <div class="info-item">
        <span class="label">Email</span>
        <span class="value">{{ props.customer.email }}</span>
      </div>
      <div class="info-item">
        <span class="label">Incidències</span>
        <span :class="['status-tag', props.customer.incidencies?.length > 0 ? 'active' : 'empty']">
          {{ props.customer.incidencies?.length || 0 }} assignades
        </span>
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

.header-info h3 {
  margin: 0;
  font-size: 1.1rem;
  color: #1f2937;
}

.id-badge {
  font-size: 0.75rem;
  color: #6b7280;
  background: #f3f4f6;
  padding: 2px 8px;
  border-radius: 12px;
}

.card-body {
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
}

.info-item {
  display: flex;
  flex-direction: column;
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