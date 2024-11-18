<script setup>
import { ref, computed } from 'vue'
import AddTodo from '../Organisms/AddTodo.vue'
import { INIT_TODO_LIST, INIT_UNIQUE_ID } from '../../constants/data'

const originTodoList = ref(INIT_TODO_LIST)
const addInputValue = ref('')
const uniqueId = ref(INIT_UNIQUE_ID)
const searchKeyword = ref('')

// 表示用のTodoリストを返す算出プロパティ
const showTodoList = computed(() => {
  return originTodoList.value.filter((todo) => {
    // 検索キーワードに部分一致したTodoだけを一覧表示する
    const regexp = new RegExp('^' + searchKeyword, 'i')
    return todo.title.match(regexp)
  })
})

const onChangeAddInputValue = (e) => {
  addInputValue.value = e.target.value
}

const handleAddTodo = (e) => {
  if ((e.key = 'Enter' && addInputValue !== '')) {
    const nextUniqueId = uniqueId + 1
    const newTodoList = [
      ...originTodoList.value,
      {
        id: nextUniqueId,
        title: addInputValue.value,
        isDone: false
      }
    ]
    originTodoList.value = newTodoList

    // 採番IDを更新
    uniqueId.value = nextUniqueId
    // todo追加後、入力値をリセット
    addInputValue.value = ''
  }
}

const handleDeleteTodo = (targetId, targetTitle) => {
  if (window.confirm(`「${targetTitle}」を削除しますか？`)) {
    const newTodoList = originTodoList.value.filter((todo) => {
      return todo.id !== targetId
    })
    originTodoList.value = newTodoList
  }
}

const handleChangeSearchKeyword = (e) => {
  searchKeyword.value = e.target.value
}
</script>

<template>
  <div class="container">
    <h1 class="title">Todo List</h1>
  </div>
  <!-- Todo追加エリア -->
  <section class="common">
    <AddTodo :addInputValue="addInputValue" :onChangeTodo="onChangeAddInputValue" :handleAddTodo="handleAddTodo" />
  </section>
  <!-- Todo フォームエリア -->
  <section class="common"></section>
  <!-- Todo 一覧表示エリア -->
  <section class="common"></section>
</template>

<style scoped>
.container {
  width: 50%;
  margin: 80px auto;
}

.title {
  text-align: center;
  font-family: 'Times New Roman', Times, serif;
  color: #fff;
  font-size: 48px;
}

.common {
  width: 80%;
  margin: 40px auto;
}
</style>
