<template>
  <article>
    <input type="checkbox" :checked="task.isCompleted" @change="toggle">
    {{ task.isCompleted ? 'ok' : 'not ok' }}
    <h2>{{ task.name }}</h2>
    <button type="button" @click="remove">x</button>
  </article>
</template>

<script>
export default {
  props: {
    task: Object,
  },
  setup(props, { emit }) {
    const remove = () => {
      emit('remove');
    };

    const toggle = () => {
      emit('toggle');
    }

    return {
      toggle,
      remove,
    };
  },
};
</script>
