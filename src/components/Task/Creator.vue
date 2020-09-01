<template>
  <form @submit.prevent="addTask">
    <input v-model="task">
    <button type="submit">Create task</button>
  </form>
</template>

<script>
import { ref } from "vue";

export default {
  setup(props, { emit }) {
    const task = ref('');

    const addTask = () => {
      emit('create', task);
    }

    return {
      task,
      addTask,
    }
  }
}
</script>
