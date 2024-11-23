<script setup>
import { defineProps, defineEmits } from 'vue'
import InputForm from '../Atoms/InputForm.vue'

defineProps({
  modelValue: {
    type: String,
    required: true
  },
  onAddTodo: {
    type: Function,
    required: true
  }
})

defineEmits(['update:modelValue'])
</script>

<template>
  <h2 class="subTitle">ADD TODO</h2>
  <InputForm
    :modelValue="modelValue"
    :placeholder="`Please input todo`"
    @update:modelValue="$emit('update:modelValue', $event)"
    :onKeydown="onAddTodo"
  />
</template>

<style scoped>
.subTitle {
  text-align: center;
  color: #fff;
}
</style>
