<template>
  <div>
    <h3>Selection example.</h3>
    <p>
      Select any part of this paragraph. You will see a context menu.
      After selecting a higlighting color the selected text will be
      higlighted.
    </p>
  </div>
</template>

<script>
import { HighlightMixin } from "@kognity/vue-yellow-marker";
import SelectionMenu from "./components/SelectionMenu";

export default {
  name: "ExampleComponent2",
  mixins: [HighlightMixin],
  data() {
    return {
      // Mixin configuration
      ymConfig: {
        menus: {
          selection: {
            component: SelectionMenu,
            actions: {
              addHighlight: this.addHighlight
            }
          }
        },
        debounceDelay: 100
      }
    };
  },
  methods: {
    addHighlight(color) {
      this.ymRemoveMenu();
      this.ymHighlightSelection(this.onHighlightClicked, { color: color });
      this.ymRemoveSelection();
    },
    onHighlightClicked() {
      alert("Highlight clicked");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
