<script setup>
defineProps(["todos"]);
const emit = defineEmits(["deleteTodo"]);
const clickRemove = (i) => emit("deleteTodo", i);
</script>

<template>
  <ul v-if="todos.length > 0">
    <li v-for="(todo, i) in todos" :key="todo">
      {{ todo }}
      <button @click="clickRemove(i)">削除</button>
    </li>
  </ul>
  <p v-else>Todoを追加してください</p>
</template>
