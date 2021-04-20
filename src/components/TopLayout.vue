<template>
  <div id="TopLayout" ref="tl">
    <div :class="['topWrapper', { filterNone: chanSelectedDelayed }]">
      <div
        class="topLayout"
        :style="`clip-path: path('M 0 ${height * 0.705521472392638} L ${
          width * 0.14583
        } ${height * 0.705521472392638} C ${width * 0.25} ${
          height * 0.705521472392638
        } ${width * 0.25} ${height * 0.8179959100204499} ${width * 0.375} ${
          height * 0.8179959100204499
        } L ${width * 0.625} ${height * 0.8179959100204499} C ${width * 0.75} ${
          height * 0.8179959100204499
        } ${width * 0.75} ${height * 0.705521472392638} ${width * 0.85416} ${
          height * 0.705521472392638
        } L ${width} ${height * 0.705521472392638} L ${width} 0 L 0 0');
        height: ${height * 0.8179959100204499}px;`"
      >
        <transition name="blackBg">
          <div v-if="chanSelected" class="blackFadedBckgrnd"></div>
        </transition>
        <div v-if="!chanSelected" id="backgroundLines">
          <div v-for="n in 100" :key="'line-' + n" class="backgroundLine"></div>
        </div>
        <Channels @channelSelected="channelSelected($event)" />
        <h1>Wii Menu</h1>
      </div>
    </div>
    <h1>Sat 23/02</h1>
  </div>
</template>

<script>
import Channels from "./Channels";

export default {
  data: function () {
    return {
      width: 1920,
      height: 1080,
      chanSelected: false,
      chanSelectedDelayed: false,
    };
  },
  methods: {
    getSize() {
      this.width = this.$refs.tl.offsetWidth;
      this.height = this.$refs.tl.offsetHeight;
    },
    channelSelected(e) {
      this.chanSelected = e;
      // because of a weird bug, filter breaks ui when resolution is higher,
      // just change chanSelectedDelayed to chanSelected in the class at line 3 to reproduce
      if (e) this.chanSelectedDelayed = e;
      else {
        setTimeout(() => {
          this.chanSelectedDelayed = e;
        }, 670);
      }
    },
  },
  mounted: function () {
    this.getSize();
    window.addEventListener("resize", this.getSize);
  },
  deactivated: function () {
    window.removeEventListener("resize", this.getSize);
  },
  components: {
    Channels,
  },
};
</script>

<style>
#TopLayout {
  height: 100vh;
}
.topWrapper {
  filter: drop-shadow(0px 5px 0px var(--wii-blue))
    drop-shadow(0px 10px 20px #00000030);
}
.filterNone {
  filter: none;
}
.topLayout {
  position: absolute;
  width: 100vw;
  height: 50rem;
  background-color: var(--top-layout);
  background-image: linear-gradient(
    90deg,
    var(--top-layout) 0%,
    var(--top-layout-gradient-light) 50%,
    var(--top-layout) 100%
  );
  clip-path: path(
    "M 0 690 L 280 690 C 480 690 480 800 720 800 L 1200 800 C 1440 800 1440 690 1640 690 L 1920 690 L 1920 0 L 0 0"
  );
  -webkit-transition: background 0.5s ease-in-out;
  transition: background 0.5s ease-in-out;
}
.topLayout h1 {
  display: flex;
  justify-content: center;
  position: absolute;
  bottom: 4%;
  margin: 0;
  left: 0;
  right: 0;
  font-weight: 400;
  color: var(--wii-blue);
  font-size: 5rem;
}
#TopLayout > h1 {
  display: flex;
  justify-content: center;
  position: absolute;
  bottom: 6rem;
  margin: 0;
  left: 0;
  right: 0;
  color: var(--font-light);
  font-size: 4rem;
}
.backgroundLine {
  width: 100%;
  height: 3px;
  margin-bottom: 9px;
  background-color: var(--top-layout-light);
}
.blackFadedBckgrnd {
  position: absolute;
  z-index: 0;
  background-color: black;
  height: 100%;
  width: 100%;
}
.blackBg-enter-active {
  animation: fadeBlack 0.3s linear;
}
.blackBg-leave-active {
  animation: fadeBlack 0.5s linear reverse;
}

@keyframes fadeBlack {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>