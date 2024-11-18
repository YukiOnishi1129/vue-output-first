<script setup>
import { defineProps } from 'vue'
import InputForm from '../Atoms/InputForm.vue'

const { addInputValue, onChangeTodo, handleAddTodo } = defineProps({
  addInputValue: String,
  onChangeTodo: Function,
  handleAddTodo: Function
})
</script>

<template>
  <h2 class="subTitle">ADD TODO</h2>
  <InputForm
    :inputValue="addInputValue"
    :placeholder="`Please input todo`"
    :handleChangeValue="onChangeTodo"
    :handleKeyDown="handleAddTodo"
  />
</template>

<style scoped>
.subTitle {
  text-align: center;
  color: #fff;
}
</style>
