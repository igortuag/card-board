<template>
  <div class="board" @mousemove="changePosition">
    {{ x }} e {{ y }}
    <div
      class="box"
      @mousedown="pickBox"
      @mouseup="dropBox"
      :style="styleObject"
    >
      <p class="positions">{{ x }} e {{ y }}</p>
      {{ clicked }}
    </div>

    <Box :posX="x" :posY="y" />
    <Box :posX="x" :posY="y" />
    <Box :posX="x" :posY="y" />
    <Box :posX="x" :posY="y" />
    <Box :posX="x" :posY="y" />
    <Box :posX="x" :posY="y" />
  </div>
</template>

<script>
import Box from "./Box";

export default {
  data() {
    return {
      x: 0,
      y: 0,
      teste: "",
      styleObject: {
        background: "red",
      },
      clicked: false,
    };
  },
  components: {
    Box,
  },
  computed: {
    PosX() {
      return 2;
    },
    PosY() {
      return 1;
    },
  },
  methods: {
    changePosition(event) {
      (this.x = parseInt(event.pageX) - 50 + "px"),
        (this.y = parseInt(event.pageY) - 50 + "px");
      this.moveBox();
    },
    pickBox() {
      this.clicked = true;
    },
    dropBox() {
      this.clicked = false;
    },
    moveBox() {
      if (this.clicked) {
        this.styleObject.top = this.y;
        this.styleObject.left = this.x;
      }
    },
  },
};
</script>

<style scoped>
.box {
  position: absolute;
  color: white;
  width: 100px;
  height: 100px;
  background: #2c3e50;
}

.box-2 {
  position: absolute;
  right: 0;
  color: white;
  width: 200px;
  height: 200px;
  background: red;
}

.positions {
  font-size: 12px;
}

.board {
  position: relative;
  background: blue;
  width: 100%;
  height: 100%;
}
</style>
