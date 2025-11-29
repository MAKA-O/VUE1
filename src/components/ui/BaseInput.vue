<template>
  <div class="input-wrapper">
    <label v-if="label" class="input-label">{{ label }}</label>
    <input
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        class="custom-input"
        v-bind="$attrs"
    />
  </div>
</template>

<script setup>
defineProps({
  label: String,
  modelValue: String
})
</script>

<style scoped>
.input-wrapper {
  margin-bottom: 15px;
  text-align: left;
}
.input-label {
  display: block;
  margin-bottom: 5px;
  font-weight: 500;
  font-size: 0.9rem;
  color: #2c3e50;
}
.custom-input {
  width: 100%;
  padding: 10px 12px;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-size: 1rem;
  box-sizing: border-box;
}
.custom-input:focus {
  outline: none;
  border-color: #42b883;
}
</style>