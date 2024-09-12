<template>
  <v-container class="board" fluid>
    <!-- TODO : 상단에 메뉴바를 만들어야 한다.  -->

    <v-card>
      <v-layout>
        <v-navigation-drawer floating permanent>
          <v-list density="compact" nav>
            <!-- TODO : 생성된 노드를 트리 구조로 보여준다. -->
            <v-list-item
              prepend-icon="mdi-view-dashboard"
              title="Home"
              value="home"
            ></v-list-item>
            <v-list-item
              prepend-icon="mdi-forum"
              title="About"
              value="about"
            ></v-list-item>
          </v-list>
        </v-navigation-drawer>
      </v-layout>
    </v-card>
    <svg id="mySvg" viewBox="0 0 2000 1000" xmlns="http://www.w3.org/2000/svg">
      <!-- Board -->
      <rect
        x="-100000"
        y="-50000"
        width="200000"
        height="100000"
        style="fill: white"
      />

      <!-- TODO : Node 를 배치해서 화면에 보여줘야 한다.  -->
      <text x="1000" y="500">Hello Ruby!</text>
    </svg>
  </v-container>
</template>

<script setup lang="ts">
import svgPanZoom from "svg-pan-zoom";

const initSvgPanZoom = () => {
  svgPanZoom("#mySvg", {
    zoomEnabled: true,
    controlIconsEnabled: true, // TODO : Icon 여부. 해당 아이콘을 css 를 통해 꾸며야한다.
    fit: true,
    center: true,
    contain: true, // svg 경계 밖으로 PanZoom 을 드래그할 수 없음
    minZoom: 0.01, // 매우 작은 배율로 축소 가능
    maxZoom: 1000, // 매우 큰 배율로 확대 가능
  });
};

onMounted(() => {
  initSvgPanZoom();
});
</script>

<style scoped>
/* SVG 스타일을 조정할 수 있습니다. */
.board {
  position: relative;
  width: 100%;
  height: 100%;
  padding: 0;
  margin: 0;
}

.v-card {
  position: absolute;
  top: 0;
  left: 0;
  width: 200px;
  height: 100%;
}

.v-layout {
  height: 100%;
}

#mySvg {
  position: absolute;
  top: 0;
  left: 200px;
  width: calc(100% - 200px);
  height: 100%;
}
</style>
