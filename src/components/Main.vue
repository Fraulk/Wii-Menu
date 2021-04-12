<template>
  <div id="MainMenu">
    <transition name="topLayoutTrans">
      <TopLayout v-if="pressed" />
    </transition>

    <SideButton @press="pressed = !pressed" />
  </div>
</template>

<script>
import TopLayout from "./TopLayout";
import SideButton from "./SideButtons";

export default {
  data() {
    return {
      pressed: true,
    };
  },
  components: {
    TopLayout,
    SideButton,
  },
};
</script>

<style>
.topLayoutTrans-enter-active {
  animation: topLayoutAppear 0.5s forwards;
}
.topLayoutTrans-leave-active {
  animation: topLayoutDisappear 0.5s forwards;
}

@keyframes topLayoutAppear {
  0% {
    transform: translateY(-90vh);
  }
  100% {
    transform: translateY(0);
  }
}
@keyframes topLayoutDisappear {
  100% {
    transform: translateY(-100vh);
  }
}
</style>