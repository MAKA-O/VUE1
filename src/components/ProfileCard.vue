<template>
  <div class="card">
    <div class="card-header">
      <div class="avatar-placeholder">{{ initials }}</div>
    </div>
    <div class="card-body">
      <h2>{{ user.name }} {{ user.surname }}</h2>
      <p class="role">{{ user.role }}</p>

      <div class="info-grid">
        <div class="info-item">
          <strong>Город:</strong> {{ user.city }}
        </div>
        <div class="info-item">
          <strong>Опыт:</strong> {{ user.experience }} лет
        </div>
      </div>

      <div class="bio-section">
        <strong>О себе:</strong>
        <p>{{ user.bio }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  user: {
    type: Object,
    required: true
  }
})

const initials = computed(() => {
  const n = props.user.name ? props.user.name[0] : ''
  const s = props.user.surname ? props.user.surname[0] : ''
  return (n + s).toUpperCase() || '?'
})
</script>

<style scoped>
.card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  width: 100%;
  max-width: 350px;
  margin: 0 auto;
}

.card-header {
  background-color: #42b883;
  height: 80px;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  padding-bottom: 20px;
  position: relative;
  margin-bottom: 30px;
}

.avatar-placeholder {
  width: 70px;
  height: 70px;
  background: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  font-weight: bold;
  color: #42b883; /* Цвет букв */
  border: 4px solid white;
  position: absolute;
  bottom: -35px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

.card-body {
  padding: 10px 20px 20px;
  text-align: center;
}

.card-body h2 {
  margin: 0 0 5px;
  color: #2c3e50;
}

.role {
  color: #42b883;
  font-weight: 600;
  font-size: 0.9rem;
  margin: 0;
}

.info-grid {
  display: flex;
  justify-content: space-between;
  margin: 20px 0;
  padding: 15px 0;
  border-top: 1px solid #eee;
  border-bottom: 1px solid #eee;
  font-size: 0.9rem;
}

.bio-section p {
  color: #666;
  margin-top: 5px;
  word-wrap: break-word;
}
</style>