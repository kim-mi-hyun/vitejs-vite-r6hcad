<!-- js -->
<script setup>
import { ref } from 'vue';

const inpuValue = ref('');
const todoList = ref([
  { text: 'veu', done: false },
  { text: 'react', done: false },
  { text: 'vercel', done: false },
]);
const inputStatus = ref('');

const handleClick = () => {
  todoList.value.push(inpuValue.value);
  inpuValue.value = '';
};

const handleDelete = (index) => {
  todoList.value.splice(index, 1);
};

const handleModify = (index) => {
  //todoList.value.splice(index, 1);
};
</script>
<!-- html -->
<template>
  <h1>Todo List</h1>

  <div>{{ todoList }}</div>
  <input v-model="inpuValue" />
  <button @click="handleClick">확인</button>

  <div class="todo-item" v-for="(item, index) in todoList">
    <input type="checkbox" v-model="item.done" />
    <span :class="{ 'done-item': item.done }">{{ item.text }}</span>
    <button @click="handleModify(index)">수정</button>
    <button @click="handleDelete(index)">삭제</button>
  </div>

  <div></div>
</template>

<style scoped>
h1 {
  color: red;
}
.todo-item {
  width: 100;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  border: 1px solid gray;
}

.done-item {
  text-decoration: line-through;
}
</style>
