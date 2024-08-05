<script setup lang="ts">
import type { Todo } from "../types";
const props = defineProps<{
  getAllTodo: Todo[]
}>();
console.log(props.getAllTodo);

function remove(index: number) {
  props.getAllTodo.splice(index, 1)
}
</script>

<template>
  <table class="table mt-3 container">
    <thead>
      <tr>
        <th scope="col">Tâche</th>
        <th scope="col">Statut</th>
        <th scope="col">Options</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="task, index in getAllTodo" :key="task.id">
        <td>
          <input class="form-check-input mx-2" type="checkbox" v-model="task.isDone" /><span
            :class="{ done: task.isDone }">{{ task.text }}</span>
        </td>
        <td>{{ task.isDone == false ? "En cours" : "Terminé" }}</td>
        <td>
          <button class="btn btn-primary mx-3" v-if="task.isDone == false">Update</button>
          <button @click="remove(index)" class="btn btn-danger">
            X
          </button>
        </td>
      </tr>
    </tbody>

  </table>

</template>

<style scoped>
.done {
  text-decoration: line-through;
  color: red;
}

.container {
  font-size: 1.5rem;
}
</style>