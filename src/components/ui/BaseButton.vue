<template>
  <button class="base-button">
    <slot></slot>
  </button>
</template>

<style scoped>
.base-button {
  background-color: #42b883;
  color: white;
  border: none;
  padding: 12px 24px;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  width: 100%;
  transition: background-color 0.2s;
}

.base-button:hover {
  background-color: #3aa876;
}
</style>