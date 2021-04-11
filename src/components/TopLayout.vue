<template>
  <div id="TopLayout">
    <div class="topWrapper">
      <div class="topLayout">
        <h1>Wii Menu</h1>
      </div>
    </div>
    <h1>Sat 23/02</h1>
  </div>
</template>

<style>
.topWrapper {
  filter: drop-shadow(0px 5px 0px #59b7d9) drop-shadow(0px 10px 20px #00000030);
}
.topLayout {
  position: absolute;
  width: 100vw;
  height: 50rem;
  background-color: #e6e6e6;
  clip-path: path(
    "M 0 690 L 280 690 C 480 690 480 800 720 800 L 1200 800 C 1440 800 1440 690 1640 690 L 1920 690 L 1920 0 L 0 0"
  );
}
.topLayout h1 {
  display: flex;
  justify-content: center;
  position: absolute;
  bottom: 2rem;
  margin: 0;
  left: 0;
  right: 0;
  font-weight: 400;
  color: #3cb9e6;
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
  color: #818181;
  font-size: 4rem;
}
</style>