<template>
  <div class="wiiButton">
    <slot></slot>
  </div>
</template>

<style >
.wiiButton {
  display: flex;
  width: 20%;
  height: 50%;
  margin-top: 5px;
  margin-bottom: 9px;
  padding: 0 15px 2px 15px;
  border: 1px solid;
  border-radius: 50px;
  border-color: var(--wii-blue);
  font-size: 40%;
  color: #2c2c2c;
  background-color: var(--top-layout);
  justify-content: center;
  align-items: center;
  box-shadow: inset -5px -10px 3px -7px #9b9b9bd8, inset 3px 7px 1px 0px #fafafa;
}
</style>