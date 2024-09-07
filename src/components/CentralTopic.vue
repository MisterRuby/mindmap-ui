<template>
  <!-- Central Topic Component -->
  <!-- TODO - 외부에서 컴포넌트 및 텍스트 크기를 변경할 수 있어야 한다. -->
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
      <path :d="calculatePath" fill="crimson"></path>
      <!-- <text
        text-anchor="middle"
        alignment-baseline="middle"
        :transform="textTransform"
      >
        {{ text }}
      </text> -->
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
const props = defineProps({
  width: {
    type: Number,
    default: 160,
    required: false,
  },
  height: {
    type: Number,
    default: 40,
    required: false,
  },
});

const text = ref<string>("");

const textTransform = computed<string>(() => {
  return `translate(${props.width / 2}, ${props.height / 2})`;
});

const viewBox = computed<string>(() => {
  return `0 0 ${props.width} ${props.height}`;
});

const calculatePath = computed<string>(() => {
  return `M0 ${props.height / 2} C0 ${props.height / 4}, ${
    props.height / 4
  } 0, ${props.height / 2} 0 L${props.width - props.height / 2} 0 C${
    props.width - props.height / 4
  } 0, ${props.width} ${props.height / 4}, ${props.width} ${
    props.height / 2
  } C${props.width} ${(props.height * 3) / 4}, ${
    props.width - props.height / 4
  } ${props.height}, ${props.width - props.height / 2} ${props.height} L${
    props.height / 2
  } ${props.height} C${props.height / 4} ${props.height}, 0 ${
    (props.height * 3) / 4
  }, 0 ${props.height / 2}`;
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
