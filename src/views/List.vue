<template>
  <div class="list">
    <div class="stats">
      <h3 class="stats__title">{{"Текущие задачи: " + tasks.length}}</h3>
    </div>

    <Task @task_done="delete_task(idx)" :data="data" v-for="(data, idx) in tasks" :key="idx"/>
    <div class="add_task">
      <div class="add_task__input">
        <input type="text" placeholder="Новая задача" v-model="new_task.title">
        <textarea placeholder="Описание" v-model="new_task.description"></textarea>
      </div>
      <button @click="add_task" class="add_task__btn">➕</button>
    </div>
  </div>
</template>

<script>

import Task from '@/components/Task.vue';

export default {
  name: 'list',
  data: () => ({
    tasks: [
      {
        title: 'Title 1',
        description: 'desc 1',
      },
      {
        title: 'Title 2',
        description: 'desc 2',
      },
    ],
    new_task: [
      {
        title: '',
        description: '',
      },
    ],
  }),
  components: {
    Task,
  },
  methods: {
    delete_task(idx) {
      this.tasks.splice(idx, 1);
    },

    add_task() {
      if (this.new_task.title !== '') {
        this.tasks.push({
          title: this.new_task.title,
          description: this.new_task.description,
        });

        this.new_task.title = '';
        this.new_task.description = '';
      }
    },
  },
};
</script>
