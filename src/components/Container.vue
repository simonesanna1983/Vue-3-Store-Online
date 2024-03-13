<script setup lang="ts">
import { ref, onMounted } from 'vue';
import List from './list/List.vue';
import Search from './search/Search.vue';
import '../styles/container.css';
import Todo from '../model/todo';

const todos = ref<Todo>([]);

const todosFiltered = ref<Todo>([]);

onMounted(() => {
  fetch('https://jsonplaceholder.typicode.com/todos')
    .then((response) => response.json())
    .then((data) => {
      // Assign the fetched data to the todos array
      todos.value = data.slice(0, 10);
      todosFiltered.value = [...todos.value];
    })
    .catch((error) => {
      console.error('Error fetching data:', error);
    });
});

function handleSearchCallBack(title: String) {
  filterByTitle(title);
}

function filterByTitle(title: String) {
  todosFiltered.value = todos.value.filter((x) => x.title.startsWith(title));

  console.log('todosFiltered.value', todosFiltered.value);
}
</script>

<template>
  <div class="container-wrapper w-75">
    <Search @searchCallBack="handleSearchCallBack" />
    <List :todos="todosFiltered" />
  </div>
</template>
