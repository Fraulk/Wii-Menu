<template>
  <div id="MainMenu">
    <TopLayout />

    <div class="sideBtns">
      <div class="leftBtn"></div>
      <div class="rightBtn"></div>
    </div>
  </div>
</template>

<script>
import TopLayout from "./TopLayout";

export default {
  components: {
    TopLayout,
  },
};
</script>

<style>
.sideBtns {
  display: flex;
  justify-content: space-between;
  position: absolute;
  bottom: 40px;
  left: 0;
  right: 0;
}
.leftBtn {
  width: 280px;
  height: 210px;
  border: inset 10px #75757530;
  border-style: ridge;
  border-left-width: 0;
  border-radius: 0 150px 150px 0;
}
.rightBtn {
  width: 280px;
  height: 210px;
  border: inset 10px #75757530;
  border-style: ridge;
  border-right-width: 0;
  border-radius: 150px 0 0 150px;
}
</style>