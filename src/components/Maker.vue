<template>
  <div class="hello">
    <h1 class="text-center bg-gray-600 text-white text-2xl">Maker</h1>
    <div class="grid grid-flow-col grid-cols-2 m-2">
      <canvas
        class="w-fit border-2 border-black"
        ref="can"
        width="800"
        height="800"
        v-on:MouseDown="onSelect"
      ></canvas>

      <div id="controls" class="bg-gray-300">
        <div class="grid grid-cols-1 gap-4 justify-center mt-12">
          <button id="addNewSquare" class="button" @click="addNewSquare">
            Add New Square
          </button>
          <select v-model="color" class="w-64 h-12 m-auto">
            <option>red</option>
            <option>green</option>
            <option>blue</option>
          </select>
          <button
            id="evenlySpaceVertically"
            class="button"
            @click="evenlySpaceVertically"
          >
            Evenly Space Vertically
          </button>
          <button
            id="getCurrentObjects"
            class="button"
            @click="getCurrentCanvasObjects"
          >
            Console Log Current Objects
          </button>
          <button id="reRenderCanvas" class="button" @click="reRenderCanvas">
            Re-Render Canvas
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { fabric } from "fabric";

export default {
  name: "Maker",
  data: () => ({
    canvas: null,
    color: "blue",
  }),
  mounted() {
    const ref = this.$refs.can;
    this.canvas = new fabric.Canvas(ref);
    const rect = new fabric.Rect({
      fill: "red",
      width: 100,
      height: 100,
      left: 0,
      top: 0,
    });
    this.canvas.add(rect);
  },
  methods: {
    addNewSquare() {
      //To be implemented

      const rectAdded = new fabric.Rect({
        fill: this.color,
        width: 100,
        height: 100,
        left: 0,
        top: 0,
      });
      this.canvas.add(rectAdded);
    },
    evenlySpaceVertically() {
      //To be implemented
    },
    reRenderCanvas() {
      this.canvas.renderAll();
    },
    getCurrentCanvasObjects() {
      console.log(this.canvas.getObjects());
      return this.canvas.getObjects();
    },
    onSelect() {
      console.log("mousedown");
  /*     this.canvas.on('mouse:down', function() {
        console.log('éve')
      }) */
    }
  },
};
</script>

<style scoped>
.button {
  @apply bg-gray-500 w-64 h-12 text-white m-auto;
}
</style>
