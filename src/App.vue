<script setup>
import { ref, computed } from "vue";
import HomeView from "./views/HomeView.vue";
import ColorButton from "./components/ColorButton.vue";
import TodoList from "./components/TodoList.vue";

// const answer = computed(() => {
//   return 123 + 456;
// })
const showName = computed(() => `ようこそ ${myname.value}さん!`);
const myname = ref("");
const style = ref("tomato");
const number = ref(null);
const countUp = () => {
  number.value++;
};

const todos = ref([]);
const newTodo = ref("");
const addTodo = () => {
  if (newTodo.value === "") return;
  todos.value.push(newTodo.value);
  newTodo.value = "";
};
const deleteTodo = (i) => {
  todos.value.splice(i, 1);
};
</script>

<template>
  <router-link to="/">Home</router-link> |
  <router-link to="/about">About</router-link>
  <HomeView />
  <p>名前は <input type="text" size="30" v-model="myname" />です</p>
  <p v-show="myname" :style="{ backgroundColor: style }">{{ showName }}</p>
  <input type="number" v-model="number" />
  <button @click="countUp">ボタン</button>
  <br />
  <form v-on:submit.prevent>
    <input type="text" v-model="newTodo" />
    <button @click="addTodo">追加</button>
  </form>
  <TodoList :todos="todos" @deleteTodo="deleteTodo" />
  <ColorButton bgColor="aquamarine">Button</ColorButton>
</template>

<style>
p {
  color: teal;
}
</style>
