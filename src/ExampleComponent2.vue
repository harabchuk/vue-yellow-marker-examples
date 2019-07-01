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
import marker from "@kognity/vue-yellow-marker";
import SelectionMenu from "./components/SelectionMenu";

export default {
  name: "ExampleComponent2",
  mixins: [marker.HighlightMixin],
  data() {
    return {
      // Mixin configuration
      hlConfig: {
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
      this.removeMenu();
      this.highlightSelection(this.onHighlightClicked, { color: color });
      this.removeSelection();
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
