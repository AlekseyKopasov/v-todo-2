<template>
  <div class="task">
    <div>
      <h3 class="task__title">{{data.title}}</h3>
      <p class="task__desc">{{data.description}}</p>
    </div>
    <button @click="task_done" class="task__done">✔️</button>
  </div>
</template>

<script>
export default {
  props: ['data'],
  methods: {
    task_done() {
      this.$emit('task_done');
    },
  },
};
</script>

<style>

</style>
