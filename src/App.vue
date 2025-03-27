<script setup lang="ts">
import { System } from "vtron";
import beaticon from "./assets/beat.ico";
import HelloVue from "./apps/Hello.vue";
import { VtronComputer } from "vtron";
import { vtronPlus } from "vtron-plus";

const system = new System({
  id:1,
  /** 内置功能
   *   | 'MyComputer':我的电脑
  | 'DataTimeTray' 日期时间托盘
  | 'BatteryTray' 电池托盘
  | 'NetworkTray' 网络托盘
  | 'ImageOpener' 图片打开器
  | 'UrlOpener' 网址打开器
  | 'TextOpener' 文本打开器
  | 'ShortCutOpener' 快捷方式打开器
  | 'ExeOpener'可执行文件打开器 
  | 'Power' 开始菜单-电源
  | 'MessageCenter' 消息中心
  | 'Setting' 开始菜单-设置
  | 'Setting-Language' 语言设置
  | 'Setting-Account' 账户设置
  | 'Setting-Personalization'; 个性化设置
   */
  builtinFeature:["MyComputer","DataTimeTray","BatteryTray","NetworkTray","ImageOpener","UrlOpener","TextOpener","ShortCutOpener","ExeOpener","Power","MessageCenter","Setting","Setting-Language","Setting-Account","Setting-Personalization"],
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
  readySystem.use(vtronPlus())
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
