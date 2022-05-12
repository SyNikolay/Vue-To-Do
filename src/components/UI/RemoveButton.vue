<template>
  <button class="remove">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "RemoveButton",
};
</script>

<style lang="scss" scoped>
.remove {
  border: none;
  padding: 5px 10px;
  color: #fff;
  font-size: 12px;
  background-color: rgb(246, 57, 57);
  cursor: pointer;
  transition: 0.1s;
  &:hover {
    background-color: rgb(255, 90, 90);
  }
  &:active {
    transform: scale(.98);
  }
}
</style>