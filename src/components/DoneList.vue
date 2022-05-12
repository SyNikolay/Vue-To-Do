<template>
  <div class="main__title">
    <h2 class="main__title-text">Сделано</h2>
    <span class="main__count">{{ doneTasks.length }}</span>
  </div>
  <div class="main__done-list" v-if="doneTasks.length > 0">
    <div class="main__todo-item" v-for="(task, i) in doneTasks" :key="task.id">
      <div class="main__check-container">
        <input
          type="checkbox"
          checked
          v-on:change="replaceToNew(i)"
        /><span></span>
        <p class="task-title">{{ task.title }}</p>
      </div>
      <RemoveButton @click="removeDoneTask(i)">Remove</RemoveButton>
    </div>
  </div>
  <div v-else class="main__todo-list-empty">
    <p class="empty-text">Список пуст</p>
  </div>
</template>

<script>
export default {
  name: "DoneList",
  props: {
    doneTasks: {
      type: Array,
      required: true,
    },
    newTasks: {
      type: Array,
      required: true,
    },
  },
  methods: {
    removeDoneTask(i) {
      setTimeout(() => {
        this.doneTasks.splice(i, 1);
      }, 50);
    },
    replaceToNew(i) {
      let replTask = this.doneTasks.splice(i, 1);
      this.newTasks.push(...replTask);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>