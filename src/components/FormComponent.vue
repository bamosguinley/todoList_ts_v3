<template>
  <input type="text" v-model="newTask" class="form-control" placeholder="Ajouter une nouvelle tâche"
    @keydown.enter="submitTask">
</template>

<script setup lang="ts">
import { ref } from "vue";
const newTask= ref<string>("");
// const newTask = defineModel<string>('newTask');
const emit = defineEmits<{
    (e:'sendTaskName',value:string):void
}>()
function submitTask(e: Event): void {
  if (newTask.value.trim()!=='') {
    emit("sendTaskName", newTask.value);
    newTask.value = '';
    console.log('données envoyé');
  }
}
</script>

<style scoped>
  input{
    padding: 10px;
  }
</style>