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
import HighlightMixin from "@kognity/vue-yellow-marker";

export default {
  name: "ExampleComponent2",
  mixins: [HighlightMixin],
  methods: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
