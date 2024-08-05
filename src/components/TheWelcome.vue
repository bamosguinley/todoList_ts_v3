<script setup lang="ts">
import Form from "../components/FormComponent.vue";
import TodoList from "../components/TodoListComponent.vue";
import { ref } from "vue";
import { nanoid } from "nanoid";
import type { Todo } from "../types";

const todos = ref<Todo[]>([
  { id: nanoid(), text: 'courir', isDone: false },
  { id: nanoid(), text: 'go', isDone: false },
  { id: nanoid(), text: 'courir', isDone: false }
]);

function getTaskName(taskName: string) {
  const newTodo: Todo = { id: nanoid(), text: taskName, isDone: false };
  todos.value.push(newTodo);
  
}


</script>

<template>
  <div class="col-md-6 container">
    <h1 class="text-center mt-1 text-bg-primary">Tasky</h1>
    <Form class="center" @sendTaskName="getTaskName" />
    <!-- <Form v-model:newTask="task"/> -->
    <TodoList :getAllTodo="todos" />
    {{ todos }}
  </div>
</template>
<style scoped>
.flex{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.border{
  border: 2px solid red;
  border-radius: 20px;
  width: auto;
}
.boxizing{
  box-sizing: border-box;
}
.container{
  margin: 0 auto;
}
</style>

