<script setup>
import { defineProps } from 'vue'
const { inputValue, placeholder, handleChangeValue, handleKeyDown } = defineProps({
  inputValue: String,
  placeholder: String,
  handleChangeValue: Function,
  handleKeyDown: Function
})
</script>

<template>
  <input
    type="text"
    class="input"
    :placeholder="placeholder"
    :value="inputValue"
    @input="handleChangeValue"
    @keydown="handleKeyDown"
  />
</template>

<style scoped>
.input {
  color: white;
  border: none;
  background: rgba(0, 0, 0, 0.2);
  width: 100%;
  height: 50px;
  padding: 10px;
  box-sizing: border-box;
  font-size: 20px;
  font-family: 'Times New Roman', Times, serif;
  border-radius: 5px;
}

.input::placeholder {
  color: #c0c0c0;
}
</style>
