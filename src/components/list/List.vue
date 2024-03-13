<script setup lang="ts">
import { ref, reactive, computed, onUpdated } from 'vue';
import '../../styles/list.css';
import Tick from '../../shared/ui/Tick.vue';
import NoResults from './NoResults.vue';
import Detail from '../detail/Detail.vue';

const { todos } = defineProps<{ todos: Todo[] }>();

const isModalOpen = ref(false);
const selectedTodo = ref<Todo>(todos);

function setSelectedTodo(id: number, todos: Todos[]) {
  console.log('todos', todos.value);

  console.log('selectedTodo', selectedTodo.value);

  const todoFound = todos.find((todo) => todo.id === id);
  if (todoFound) {
    selectedTodo.value = todoFound;
  }
  console.log('selectedTodo', selectedTodo.value);
}

function handleCloseModalCallBack() {
  isModalOpen.value = false;
}
function handleOpenModal(id: number, todos: Todos[]) {
  setSelectedTodo(id, todos);
  isModalOpen.value = true;
}
</script>

<template>
  <div>
    <!-- <pre>{{ JSON.stringify(todos, null, 2) }}</pre> -->

    <Detail
      :todo="selectedTodo"
      :isModalOpen="isModalOpen"
      @closeModal="handleCloseModalCallBack"
    />

    <NoResults v-if="todos.length === 0" msg="No Todos to show" />

    <table v-if="todos.length > 0" class="table table-striped">
      <thead>
        <tr>
          <th scope="col">Id</th>
          <th scope="col">Title</th>
          <th scope="col">Completed</th>
          <th scope="col"></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="todo in todos" :key="todo.id">
          <th scope="row">{{ todo.id }}</th>
          <td>{{ todo.title }}</td>
          <!-- <td>{{ todo.completed }}</td> -->
          <td><Tick :isCompleted="todo.completed" /></td>
          <td>
            <button
              @click="handleOpenModal(todo.id, todos)"
              class="btn-edit"
              type="button"
            >
              ✏️
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.btn-edit {
  border: 0;
  background-color: transparent;
}
</style>
