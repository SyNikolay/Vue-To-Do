<template>
  <div class="main__title">
    <h2 class="main__title-text">Нужно сделать</h2>
    <span class="main__count">{{ this.newTasks.length }}</span>
  </div>
  <div class="main__todo-list" v-if="newTasks.length > 0">
    <div class="main__todo-item" v-for="(task, i) in newTasks" :key="task.id">
      <div class="main__check-container">
        <input type="checkbox" v-on:change="replaceToDone(i)" /><span></span>
        <p class="task-title">{{ task.title }}</p>
      </div>
      <RemoveButton @click="removeNewTask(i)">Remove</RemoveButton>
    </div>
  </div>
  <div v-else class="main__todo-list-empty">
    <p class="empty-text">Список пуст</p>
  </div>
</template>

<script>
export default {
  name: "TaskList",
  props: {
    newTasks: {
      type: Array,
      required: true,
    },
    doneTasks: {
      type: Array,
      required: true,
    },
  },
  methods: {
    removeNewTask(i) {
      setTimeout(() => {
        this.newTasks.splice(i, 1);
      }, 50);
    },
    replaceToDone(i) {
      let replTask = this.newTasks.splice(i, 1);
      this.doneTasks.push(...replTask);
    },
  },
};
</script>

<style lang="scss" scoped>
.main {
  &__title {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid rgba(128, 128, 128, 0.815);
  }

  &__title-text {
    font-size: 18px;
    font-weight: normal;
    margin: 10px 0px;
  }

  &__count {
  }

  &__todo-list {
  }

  &__todo-list-empty {
    display: flex;
    justify-content: center;
  }

  &__todo-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 15px;
  }

  &__check-container {
    display: flex;
    align-items: center;
  }
}
</style>