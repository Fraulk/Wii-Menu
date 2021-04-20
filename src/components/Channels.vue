<template>
  <div class="channels" ref="channels">
    <div v-for="i in 4" :key="'channelRow-' + i" class="channelColumn">
      <div
        v-for="n in 3"
        :key="'channel-' + n"
        class="channel empty"
        :style="`clip-path: path('M ${width * 0.00627352572145} ${
          height * 0.0152027
        } C ${width * 0.00627352572145} 0 ${width * 0.2371392722710163} 0 ${
          width * 0.2371392722710163
        } ${height * 0.0152027} C ${width * 0.2434127979924718} ${
          height * 0.0152027
        } ${width * 0.2434127979924718} ${height * 0.30405} ${
          width * 0.2371392722710163
        } ${height * 0.30405} C ${width * 0.2371392722710163} ${
          height * 0.3192567
        } ${width * 0.00627352572145} ${height * 0.3192567} ${
          width * 0.00627352572145
        } ${height * 0.30405} C 0 ${height * 0.30405} 0 ${height * 0.0152027} ${
          width * 0.00627352572145
        } ${height * 0.0152027}');`"
      >
        <div
          @click.self="
            currentChannel = 'c' + i + '_' + n;
            showChannel(true);
          "
          v-if="i == 1 && n == 1"
          class="channelJim"
          ref="chnnl"
        >
          <div v-if="channels.c1_1 == true">
            <div class="channelBottomBar">
              <WiiButton @click="showChannel(false)">Wii Menu</WiiButton>
              <WiiButton>Start</WiiButton>
            </div>
          </div>
        </div>
        <div v-else>
          <div class="channelLines">
            <div
              v-for="chnlLne in 20"
              :key="'chnlLine-' + chnlLne"
              class="channelLine"
            ></div>
          </div>
          <div class="channelTitle">Wii</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { zoom } from "../helpers/zoom.js"; //https://github.com/hakimel/zoom.js
import WiiButton from "./WiiButton";

export default {
  data: function () {
    return {
      width: 1594,
      height: 592,
      channels: {
        c1_1: false,
        c1_2: false,
      },
      currentChannel: "",
    };
  },
  methods: {
    getSize() {
      this.width = this.$refs.channels.offsetWidth;
      setTimeout(() => {
        this.height = this.$refs.channels.offsetHeight;
      }, 10);
    },
    showChannel(channel) {
      if (channel) {
        this.channels[this.currentChannel] = true;
        this.$emit("channelSelected", true);
        this.zoomIn();
      } else if (!channel) {
        console.log("got in the false");
        this.channels[this.currentChannel] = false;
        this.$emit("channelSelected", false);
        this.zoomOut();
      }
    },
    zoomIn: function () {
      return zoom.to({
        element: this.$refs.chnnl,
        pan: false,
      });
    },
    zoomOut: function () {
      return zoom.out();
    },
  },
  mounted: function () {
    this.getSize();
    window.addEventListener("resize", this.getSize);
    this.root = document.documentElement;
  },
  deactivated: function () {
    window.removeEventListener("resize", this.getSize);
  },
  components: {
    WiiButton,
  },
};
</script>

<style>
.channels {
  position: absolute;
  top: 10%;
  left: 0;
  right: 0;
  margin: auto;
  width: 83%;
  height: 74%;
  display: flex;
  flex-direction: row;
}
.channelColumn {
  width: 25%;
  height: 100%;
  display: flex;
  flex-direction: column;
  filter: drop-shadow(3px 0px 0px #979797) drop-shadow(-3px 0px 0px #979797)
    drop-shadow(0px 3px 0px #979797) drop-shadow(0px -3px 0px #979797);
}
.channel {
  width: 98%;
  height: 32%;
  margin: auto;
  background-color: var(--empty-channel);
  clip-path: path(
    "M 10 9 C 10 0 378 0 378 9 C 388 9 388 180 378 180 C 378 189 10 189 10 180 C 0 180 0 9 10 9"
  );
}
.channel.empty {
  font-size: 2.5rem;
  color: var(--font-light);
  position: relative;
}
.channelLine {
  width: 100%;
  height: 3px;
  margin-bottom: 9px;
  background-color: #d1d1d1;
}
.channelLines {
  display: flex;
  flex-direction: column;
  animation: linesGoesUppp 1s linear infinite;
}
.channelTitle {
  position: absolute;
  display: flex;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  justify-content: center;
  align-items: center;
  color: #8181812c;
  background: url("~@/assets/noise.png");
}
.channelJim {
  height: 100%;
  background: url("~@/assets/jim.jpg") center / cover no-repeat;
  cursor: pointer;
  position: relative;
}
.channelBottomBar {
  position: absolute;
  bottom: 0;
  height: 30%;
  background-color: var(--top-layout);
  left: 0;
  right: 0;
  border-top: 1px solid #000000e7;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  cursor: auto;
  animation: bottomBar 1s forwards;
}

@keyframes linesGoesUppp {
  100% {
    transform: translateY(-12px);
  }
}

@keyframes bottomBar {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
