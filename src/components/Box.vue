<template>
  <div
    class="box-board"
    :style="styleBox"
    @mousedown="pickBox"
    @mouseup="dropBox"
    @mousemove="moveBox"
  >
    <p class="postion">{{ posX }} e {{ posY }}</p>
    {{ clicked }}
  </div>
</template>

<script>
export default {
  props: {
    posX: String,
    posY: String,
  },
  data() {
    return {
      styleBox: {
        color: "red",
      },
      clicked: false,
    };
  },
  methods: {
    pickBox() {
      this.clicked = true;
    },
    dropBox() {
      this.clicked = false;
    },
    moveBox() {
      if (this.clicked) {
        this.styleBox.position = "absolute";
        this.styleBox.top = this.posY;
        this.styleBox.left = this.posX;
      }
    },
  },
};
</script>

<style scoped>
.box-board {
  color: white;
  width: 100px;
  height: 100px;
  background: #902990;
  right: 0px;
}
</style>
