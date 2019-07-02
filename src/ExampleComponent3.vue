<template>
  <div>
    <h3>Highlighting with context menu.</h3>
    <p>
      Click on any colored highlight in this paragraph to see the context menu.
      Selecting the color from menu will change the highlight color.
    </p>
  </div>
</template>

<script>
import { HighlightMixin } from "@kognity/vue-yellow-marker";
import SelectionMenu from "./components/SelectionMenu";

export default {
  name: "ExampleComponent",
  mixins: [HighlightMixin],
  data() {
    return {
      currentHighlightContext: null,
      currentHighlightElement: null,
      // Mixin configuration
      hlConfig: {
        menus: {
          highlight: {
            component: SelectionMenu,
            actions: {
              addHighlight: this.changeHighlight
            }
          }
        },
        debounceDelay: 100
      }
    };
  },
  mounted() {
    // Example of highlighting text using the Mixin's API method 'highlight'
    const textQuote = {
      prefix: "",
      exact: "Click",
      suffix: " on any"
    };
    this.highlight(
      textQuote,
      this.onHighlightClicked,
      { color: "#FFB036" },
      {}
    );

    const textQuote2 = {
      prefix: "see the ",
      exact: "context menu",
      suffix: "."
    };
    this.highlight(
      textQuote2,
      this.onHighlightClicked,
      { color: "#FF6AD7" },
      {}
    );

    const textQuote3 = {
      prefix: "colored ",
      exact: "highlight",
      suffix: " in this"
    };
    this.highlight(
      textQuote3,
      this.onHighlightClicked,
      { color: "#FF6AD7" },
      {}
    );
  },
  methods: {
    onHighlightClicked(event, context, highlightElement) {
      this.currentHighlightContext = context;
      this.currentHighlightElement = highlightElement;
      this.createHighlightMenu(context.nodes);
    },
    changeHighlight(color) {
      if(this.currentHighlightElement) {
        this.currentHighlightElement.color = color;
      }
      this.removeMenu();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
