<script setup lang="ts">
import { System } from 'vtron'
import beaticon from "./assets/beat.ico";
import HelloVue from './apps/Hello.vue';
const system = new System({
    desktop: [
        {
            name:"Hello",
            icon:beaticon,
            window:{
                title:'Hello',
                icon:beaticon,
                width: 800,
                height: 600,
                center: true,
                content:HelloVue
            }
        }
    ]
});
system.whenReady().then((readySystem) => {
    console.log(readySystem.version);
});
</script>

<template>
  <div class="outer">
    <!-- 一定需要引入Win10组件，组件已经在use时注册了 -->
    <Screen></Screen>
  </div>
</template>
<style scoped>
.outer {
  width: 100vw;
  height: 100vh;
}
</style>
