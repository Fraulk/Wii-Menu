<template>
  <div id="MainMenu">
    <TopLayout />

    <SideButton />
  </div>
</template>

<script>
import TopLayout from "./TopLayout";
import SideButton from "./SideButtons";

export default {
  components: {
    TopLayout,
    SideButton,
  },
};
</script>

<style>
</style>