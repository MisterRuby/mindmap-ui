<template>
  <!-- <HelloWorld /> -->
  <!-- <div class="fill-height">
    <Node
      v-for="node in nodes"
      :key="node.text"
      :x="node.x"
      :y="node.y"
      :width="node.width"
      :height="node.height"
      :text="node.text"
      :fill="node.fill"
    ></Node>
  </div> -->
  <Board />
</template>

<script lang="ts" setup>
const nodes = ref<object>([
  {
    x: 0,
    y: 0,
    text: "test1",
  },
  {
    x: 100,
    y: 50,
    width: 300,
    height: 45,
    text: "test2",
    fill: "dodgerblue",
  },
]);
</script>

<style>
.fill-height {
  width: 100%;
  height: 100%;
}
</style>
