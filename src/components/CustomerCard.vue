<script setup>

const props = defineProps( {
  customer: {
    type: Object,
    required: true
  }
});

</script>

<template>
    <div class="customer-card" v-if="props.customer">
      <div class="card-header">
        <div class="avatar">
          {{ props.customer.firstName.charAt(0) }}{{ props.customer.lastName.charAt(0) }}
        </div>
        <div class="header-info">
          <h3>{{ props.customer.firstName }} {{ props.customer.lastName }}</h3>
          <span class="id-badge">ID: #{{ props.customer.id }}</span>
        </div>
      </div>
    
    <div class="card-body">
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
    </div>   
  </div>
</template>

<style scoped>
.customer-card {
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  padding: 1.5rem;
  transition: transform 0.2s, box-shadow 0.2s;
  border: 1px solid #f0f0f0;
  max-width: 350px;
}

.customer-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

.card-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

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
  font-size: 0.7rem;
  text-transform: uppercase;
  color: #9ca3af;
  letter-spacing: 0.05em;
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

.btn-detail {
  width: 100%;
  margin-top: 1.5rem;
  padding: 0.6rem;
  background: #ffffff;
  border: 1px solid #e5e7eb;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 500;
  transition: all 0.2s;
}

.btn-detail:hover {
  background: #f9fafb;
  border-color: #d1d5db;
}
</style>