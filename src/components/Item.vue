<script>
export default {
  name: 'Item',
  props: ['data'],
}
</script>

<template>
  <div
      class="item"
      v-if="data"
      v-text="data.name"
  />
</template>

<style lang="scss" scoped>
.item {
  padding: 10px;
  border: #ccc 1px solid;
  cursor: pointer;
  &.selected {
    background: #333;
  }
}
</style>
