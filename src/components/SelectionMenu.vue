<template>
  <context-menu ref="context">
    <div slot="menuBody" class="flexContainer">
      <div
        class="option"
        role="button"
        @touchend="addHighlight($event, color1)"
        @mouseup="addHighlight($event, color1)"
      >{{ 'Highlight' }}</div>
      <span class="optionDivider"/>
      <div
        class="circle"
        :style="{'background-color': color2}"
        role="button"
        @touchend="addHighlight($event, color2)"
        @mouseup="addHighlight($event, color2)"
      ></div>
      <span class="optionDivider"/>
      <div
        class="circle"
        :style="{'background-color': color3}"
        role="button"
        @touchend="addHighlight($event, color3)"
        @mouseup="addHighlight($event, color3)"
      ></div>
    </div>
  </context-menu>
</template>

<script>
import ContextMenu from "./ContextMenu";

export default {
  name: "SelectionMenu",
  components: {
    ContextMenu
  },
  data() {
    return {
      color1: "#FFB036",
      color2: "#FF6AD7",
      color3: "#F2FF7E"
    };
  },
  methods: {
    addHighlight(event, color) {
      event.stopPropagation();
      this.$emit("addHighlight", color);
    }
  }
};
</script>

<style scoped>
.option {
  cursor: pointer;
  padding: 10px 15px;
  user-select: none;
  -moz-user-select: none;
}

.optionDivider {
  border-left: 1px solid grey;
  margin: 8px 0;
}

.flexContainer {
  display: flex;
}

.circle {
  cursor: pointer;
  margin: 12px 10px 0 10px;
  width: 16px;
  height: 16px;
  border-radius: 50%;
}
</style>
