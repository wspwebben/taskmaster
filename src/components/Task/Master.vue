<template>
  <TaskCreator
    @create="createTask"
  />
  <ul>
    <li v-for="task in tasks" :key="task.name">
      <TaskItem :task="task" @toggle="toggleTask(task)" @remove="removeTask(task)"/>
    </li>
  </ul>
</template>

<script>
import { ref } from "vue";

import TaskCreator from "./Creator.vue";
import TaskItem from "./Item.vue";

export default {
  components: {
    TaskCreator,
    TaskItem,
  },
  setup() {
    const tasks = ref([]);

    const createTask = name => {
      const task = {
        name: name.value,
        isCompleted: false,
      };

      tasks.value = [...tasks.value, task];
    }

    const toggleTask = (task) => {
      tasks.value = tasks.value.map(oldTask => oldTask === task ? {
        ...task,
        isCompleted: !task.isCompleted,
      } : oldTask);
    }

    const removeTask = (task) => {
      tasks.value = tasks.value.filter(oldTask => oldTask !== task);
    }

    return {
      tasks,
      createTask,
      toggleTask,
      removeTask,
    }
  }
}
</script>
