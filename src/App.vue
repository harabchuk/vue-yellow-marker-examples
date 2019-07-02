<template>
  <div id="app">
    <ExampleComponent/>
    <ExampleComponent2/>
    <ExampleComponent3/>
  </div>
</template>

<script>
import ExampleComponent from "./ExampleComponent";
import ExampleComponent2 from "./ExampleComponent2";
import ExampleComponent3 from "./ExampleComponent3";

export default {
  name: "App",
  components: {
    ExampleComponent,
    ExampleComponent2,
    ExampleComponent3
  }
};
</script>

<style>
body {
  font-family: Helvetica, Arial sans-serif;
  font-size: 14px;
  line-height: 1.4em;
}
</style>
