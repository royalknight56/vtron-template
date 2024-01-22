<template>
  <div>Hello This child window</div>
  <div>
    {{ browserWindow.config?.message }}
  </div>
</template>
<script setup lang="ts">
import { BrowserWindow } from "vtron";
import { inject } from "vue";
const browserWindow = inject<BrowserWindow>("browserWindow")!;
</script>
