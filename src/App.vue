<template>
  <div class="app-container">
    <h1 class="main-title">Создатель Профиля</h1>

    <div class="content-wrapper">

      <div class="form-panel">
        <h3>Введите данные</h3>
        <form @submit.prevent="handleSubmit">
          <BaseInput
              v-model="formData.name"
              label="Имя"
              required
          />
          <BaseInput
              v-model="formData.surname"
              label="Фамилия"
              required
          />
          <BaseInput
              v-model="formData.role"
              label="Должность"
          />
          <BaseInput
              v-model="formData.city"
              label="Город"
          />
          <BaseInput
              v-model="formData.experience"
              label="Опыт (лет)"
              type="number"
          />
          <BaseInput
              v-model="formData.bio"
              label="Коротко о себе"
          />

          <BaseButton type="submit">
            Сгенерировать Профиль
          </BaseButton>
        </form>
      </div>

      <div class="result-panel">
        <div v-if="!submittedUser" class="empty-state">
          <p>Заполните форму</p>
        </div>
        <ProfileCard v-else :user="submittedUser" />
      </div>

    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import BaseInput from './components/ui/BaseInput.vue'
import BaseButton from './components/ui/BaseButton.vue'
import ProfileCard from './components/ProfileCard.vue'

const formData = reactive({
  name: '',
  surname: '',
  role: '',
  city: '',
  experience: '',
  bio: ''
})

const submittedUser = ref(null)

const handleSubmit = () => {
  submittedUser.value = { ...formData }
  Object.keys(formData).forEach(key => {
    formData[key] = ''
  })
}
</script>

<style>
.app-container {
  max-width: 900px;
  margin: 40px auto;
  padding: 20px;
  text-align: center;
}

.main-title {
  color: #2c3e50;
  margin-bottom: 40px;
  font-weight: 400;
  font-size: 2rem;
}

.content-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: start;
}

@media (max-width: 768px) {
  .content-wrapper {
    grid-template-columns: 1fr;
  }
}

.form-panel {
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.05);
}

.form-panel h3 {
  margin-top: 0;
  color: #42b883;
}

.result-panel {
  display: flex;
  justify-content: center;
  align-items: flex-start;
}

.empty-state {
  color: #999;
  border: 2px dashed #ccc;
  padding: 20px;
  border-radius: 12px;
  width: 100%;
}
</style>