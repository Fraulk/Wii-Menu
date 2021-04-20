<template>
  <div class="sideBtns">
    <div class="btnContainer leftBtnContainer">
      <div class="wiiSideButton leftSide">Wii</div>
    </div>
    <div class="btnContainer rightBtnContainer">
      <div @click="$emit('press')" class="wiiSideButton rightSide"></div>
    </div>
  </div>
</template>

<style>
.sideBtns {
  display: flex;
  justify-content: space-between;
  position: absolute;
  bottom: 40px;
  left: 0;
  right: 0;
}
.btnContainer {
  width: 280px;
  height: 210px;
  border: inset 10px #75757520;
  border-style: ridge;
  display: flex;
  align-items: center;
}
.leftBtnContainer {
  border-radius: 0 150px 150px 0;
  border-left-width: 0;
  justify-content: flex-end;
}
.rightBtnContainer {
  border-radius: 150px 0 0 150px;
  border-right-width: 0;
}
.wiiSideButton {
  width: 180px;
  height: 180px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 20px;
  margin-bottom: 10px;
  border: 3px solid #3cb9e6;
  border-radius: 100%;
  background-image: radial-gradient(circle at 0% 0%, #e4e4e4 30%, #bbbbbb 70%);
  box-shadow: 8px 8px 0px #00000030;
  color: var(--font-light);
  font-size: 2rem;
}
/* .wiiSideButton.leftSide {
}
.wiiSideButton.rightSide {
} */
</style>