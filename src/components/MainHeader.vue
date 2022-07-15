<template>
  <nav class="navbar navbar-light bg-light">
    <div class="container-fluid">
      <h2 class="font-weight-bold navbar-text">Call it brain dump</h2>
      <Button type="submit" text="Add Entry" color="green" />
    </div>
  </nav>
</template>

<script>
import Button from "./Button.vue";

export default {
  name: "MainHeader",
  components: { Button },
};
</script>

<style scoped>
h2 {
  text-transform: uppercase;
}
</style>
