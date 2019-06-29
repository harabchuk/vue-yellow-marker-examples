<template>
  <div>
    <h3>Highlighting example.</h3>
    <p>
      Parts of this text are highlighted with different colors.
      You can click on any highlight.
    </p>
  </div>
</template>

<script>
import HighlightMixin from "@kognity/vue-yellow-marker";

export default {
  name: "ExampleComponent",
  mixins: [HighlightMixin],
  mounted() {
    // Example of highlighting text using the Mixin's API method 'highlight'
    const textQuote = { prefix: "", exact: "Parts", suffix: " of this" };
    this.highlight(
      textQuote,
      this.onHighlightClicked,
      { color: "#FFB036" },
      {}
    );

    const textQuote2 = {
      prefix: "text are ",
      exact: "highlighted with",
      suffix: " different"
    };
    this.highlight(
      textQuote2,
      this.onHighlightClicked,
      { color: "#FF6AD7" },
      {}
    );
  },
  methods: {
    onHighlightClicked() {
      alert("Highlight clicked");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
