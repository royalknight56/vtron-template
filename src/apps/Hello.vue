<template>
  Hello
  <button @click="openWindow">打开新窗口</button>
  <button @click="openDialog">打开新对话框</button>
  <button @click="openNotify">打开新提醒</button>
</template>
<script setup lang="ts">
import { BrowserWindow, Dialog, Notify } from "vtron";
import beaticon from "../assets/beat.ico";
import HelloSubVue from "../browserWindow/HelloSub.vue";
function openWindow() {
  let bw = new BrowserWindow({
    title: "HelloSub",
    icon: beaticon,
    width: 800,
    height: 600,
    center: true,
    content: HelloSubVue,
    config: {
      message: "Config from Hello.vue",
    },
  });
  bw.show();
}
function openDialog() {
  Dialog.showMessageBox({
    title: "Hello",
    message: "Hello World!",
  });
}
function openNotify() {
  new Notify({
    title: "Hello",
    content: "Hello World!",
  });
}
</script>
