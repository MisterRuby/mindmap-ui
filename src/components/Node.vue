<template>
  <!-- Node Component -->
  <!-- TODO - 텍스트 크기를 변경할 수 있어야 한다. -->
  <!-- TODO - Node 에 대한 크기, 좌표, 텍스트 등 컴포넌트에 대한 내용을 DB 에 저장하여 불러올 때 적용한다. -->
  <div class="container" :style="containerStyle">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      :width="width"
      :height="height"
      :viewBox="viewBox"
    >
      <rect
        :x="x"
        :y="y"
        :width="width"
        :height="height"
        :rx="height / 2"
        :ry="height / 2"
        :fill="fill"
      ></rect>
    </svg>
    <input
      class="text"
      type="text"
      :value="text"
      placeholder="Please enter the central topic"
    />
  </div>
</template>
<script setup lang="ts">
const { x, y, width, height, text, fill } = defineProps({
  x: {
    type: Number,
    default: 100,
  },
  y: {
    type: Number,
    default: 100,
  },
  width: {
    type: Number,
    default: 120,
  },
  height: {
    type: Number,
    default: 40,
  },
  text: {
    type: String,
    default: "",
  },
  fill: {
    type: String,
    default: "crimson",
  },
});

const containerStyle = computed<object>(() => {
  return {
    position: "absolute",
    left: `${x}px`,
    top: `${y}px`,
    width: `${width}px`,
    height: `${height}px`,
  };
});

const viewBox = computed<string>(() => {
  return `${x} ${y} ${width} ${height}`;
});
</script>

<style scoped>
.container {
  position: absolute;
}

.text {
  text-align: center;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 100%;
  height: 100%;
}
</style>
