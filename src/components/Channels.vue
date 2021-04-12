<template>
  <div class="channels">
    <div v-for="i in 4" :key="'channelRow-' + i" class="channelColumn">
      <div class="channel empty">Wii</div>
      <div class="channel empty">Wii</div>
      <div class="channel empty">Wii</div>
    </div>
  </div>
</template>

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
  background-color: #cacaca;
  clip-path: path(
    "M 8 7 C 8 -2 376 -1 376 7 C 386 7 386 178 376 178 C 376 187 8 187 8 178 C -2 178 -2 7 8 7"
  );
}
.channel.empty {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 2.5rem;
  color: var(--font-light);
}
</style>
