<template>
  <div id="TopLayout" ref="tl">
    <div class="topWrapper">
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
        <h1>Wii Menu</h1>
      </div>
    </div>
    <h1>Sat 23/02</h1>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      width: 1920,
      height: 1080,
    };
  },
  methods: {
    getSize() {
      this.width = this.$refs.tl.offsetWidth;
      this.height = this.$refs.tl.offsetHeight;
    },
  },
  mounted: function () {
    this.getSize();
    window.addEventListener("resize", this.getSize);
  },
  deactivated: function () {
    window.removeEventListener("resize", this.getSize);
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
.topLayout {
  position: absolute;
  width: 100vw;
  height: 50rem;
  background-color: var(--top-layout);
  clip-path: path(
    "M 0 690 L 280 690 C 480 690 480 800 720 800 L 1200 800 C 1440 800 1440 690 1640 690 L 1920 690 L 1920 0 L 0 0"
  );
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
</style>