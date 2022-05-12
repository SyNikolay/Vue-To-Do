<template>
  <button class="button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "AddButton",
};
</script>

<style lang="scss" scoped>
.button {
  background-color: #12c0dd;
  border: 1px solid #12c0dd;
  color: #fff;
  font-weight: 700;
  text-transform: uppercase;
  padding: 10px 15px;
  font-size: 12px;
  height: 40px;
  outline: none;
  transition: 0.1s;
  cursor: pointer;

  &:hover {
    background-color: #0dd6f8;
    border-color: #0dd6f8;
  }
  &:active {
    transform: scale(0.98);
  }
}
</style>