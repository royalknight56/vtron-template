<script setup lang="ts">
import { System } from "vtron";
import beaticon from "./assets/beat.ico";
import HelloVue from "./apps/Hello.vue";
import { VtronComputer } from "vtron";
const system = new System({
  /** 内置功能 */
  builtinFeature:['MyComputer','ExeOpener','BatteryTray','DataTimeTray','ImageOpener','NetworkTray','ShortCutOpener','TextOpener','UrlOpener'],
  /** 桌面软件，添加后需要左下角点击恢复 */
  desktop: [
    {
      name: "Hello",
      icon: beaticon,
      window: {
        title: "Hello",
        icon: beaticon,
        width: 800,
        height: 600,
        center: true,
        content: HelloVue,
      },
    },
    {
      name: "软件组",
      type: "group",
      group: [
        {
          name: "Hello",
          icon: beaticon,
          window: {
            title: "Hello",
            icon: beaticon,
            width: 800,
            height: 600,
            center: true,
            content: HelloVue,
          },
        },
      ],
    },
  ],
});

system.whenReady().then((readySystem) => {
  console.log(readySystem.version);
});
</script>

<template>
  <div class="outer">
    <!-- 一定需要引入Win10组件，组件已经在use时注册了 -->
    <VtronComputer :system="system"></VtronComputer>
  </div>
</template>
<style scoped>
.outer {
  width: 100vw;
  height: 100vh;
}
</style>
