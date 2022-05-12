<template>
  <header class="header">
    <h1 class="header__title">To Do List</h1>
    <div class="header__content">
      <input
        class="header__task-input"
        type="text"
        v-model="title"
        @keydown.enter="addNewTask"
      />
      <AddButton @click="addNewTask" type="button"> Add New Task </AddButton>
    </div>
  </header>
</template>

<script>
export default {
  name: "MainHeader",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addNewTask() {
      let newObj = {
        id: Math.random(),
        title: this.title,
      };
      this.$emit("create", newObj);
      this.title = "";
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #333;
  padding: 10px 40px;
  margin-bottom: 10px;
  &__title {
    color: #ddd;
    margin: 0px 0px 0px 0px;
  }
  &__task-input {
    padding: 10px 5px;
    margin-right: 10px;
    outline: none;
  }
}
</style>