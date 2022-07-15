<script setup>
import { RouterLink, RouterView } from "vue-router";
import MainHeader from "./components/MainHeader.vue";
import EntryList from "./components/EntryList.vue";
import Counter from "./components/Counter.vue";
</script>

<template>
<MainHeader/>

<EntryList :entries="entries" />

<Counter />

</template>

<style>
body {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
</style>
