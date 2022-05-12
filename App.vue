<template>
  <div class="wrapper">
    <MainHeader @create="addNewTask"></MainHeader>
    <main class="main">
      <TaskList v-model:newTasks="newTasks" v-model:doneTasks="doneTasks" />
      <DoneList v-model:doneTasks="doneTasks" v-model:newTasks="newTasks" />
    </main>
  </div>
</template>

<script>
import MainHeader from "@/components/MainHeader.vue";
import TaskList from "@/components/TaskList.vue";
import DoneList from "@/components/DoneList.vue";

export default {
  data() {
    return {
      newTasks: [

      ],
      doneTasks: [

      ],
    };
  },
  components: {
    MainHeader,
    TaskList,
    DoneList,
  },
  methods: {
    addNewTask(newObj) {
      this.newTasks.push(newObj);
    },
  },
};
</script>

<style lang="scss" >
body {
  margin: 0px 0px 0px 0px;
}
.wrapper {
  max-width: 800px;
  margin: auto;
  font-family: "Ubuntu", sans-serif;
}

.main {
  max-width: 720px;
  margin: 0 auto;
  padding: 0 10px;
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
    color: rgb(9, 45, 62);
    font-size: 18px;
    line-height: 16px;
    border: 1px solid rgb(9, 45, 62);
    border-radius: 45%;
    padding: 4px 10px 6px;
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

  &__done-list {
    opacity: 0.7;
  }

  &__done-item {
  }
}

.empty-text {
  font-size: 18px;
  color: rgba(128, 128, 128, 0.673);
  margin: 25px 0;
}

input[type="checkbox"]:checked,
input[type="checkbox"]:not(:checked) {
  position: absolute;
  z-index: 1;
  opacity: 0;
  width: 20px;
  height: 20px;
  margin-top: 6px;
}
input[type="checkbox"]:checked + span,
input[type="checkbox"]:not(:checked) + span {
  position: relative;
  padding-left: 35px;
  cursor: pointer;
}
input[type="checkbox"]:checked + span::before {
  content: "";
  position: absolute;
  width: 16px;
  height: 16px;
  left: 0;
  top: calc(50% - 10px);
  background-color: transparent;
  border-radius: 2px;
  border: 2px solid #4fc1de;
}
input[type="checkbox"]:checked + span::after {
  content: "";
  position: absolute;
  width: 12px;
  height: 12px;
  transition: all 0.2s ease;
  opacity: 1;
  left: 4px;
  top: calc(50% - 6px);
  background-color: #4fc1de;
}
input[type="checkbox"]:not(:checked) + span::before {
  content: "";
  position: absolute;
  width: 16px;
  height: 16px;
  left: 0;
  top: calc(50% - 10px);
  background-color: transparent;
  border-radius: 2px;
  border: 2px solid #5d575f;
}
input[type="checkbox"]:not(:checked) + span::after {
  content: "";
  position: absolute;
  width: 12px;
  height: 12px;
  transition: all 0.2s ease;
  opacity: 0;
  left: 4px;
  top: calc(50% - 6px);
  background-color: #7d25a9;
}
</style>
