<template>
  <!-- Node Component -->
  <!-- TODO - 텍스트 크기를 변경할 수 있어야 한다. -->
  <!-- TODO - Node 에 대한 크기, 좌표, 텍스트 등 컴포넌트에 대한 내용을 DB 에 저장하여 불러올 때 적용한다. -->
  <div
    class="container"
    :style="{ width: props.width + 'px', height: props.height + 'px' }"
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      :width="props.width"
      :height="props.height"
      :viewBox="viewBox"
    >
      <rect
        x="0"
        y="0"
        :width="props.width"
        :height="props.height"
        :rx="props.height / 2"
        :ry="props.height / 2"
        :fill="props.fill"
      ></rect>
    </svg>
    <input
      class="text"
      type="text"
      :value="props.text"
      placeholder="Please enter the central topic"
    />
  </div>
</template>
<script setup lang="ts">
const props = defineProps({
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

const viewBox = computed<string>(() => {
  return `0 0 ${props.width} ${props.height}`;
});
</script>

<style scoped>
.container {
  position: relative;
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
