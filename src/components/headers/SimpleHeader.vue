<script setup lang="ts">
import { useAppConfig } from "@/composables/useAppConfig";

const { isDrawerOpen } = useAppConfig();
</script>

<template>
  <header class="header">
    <div @click="isDrawerOpen = !isDrawerOpen">
				<img src="@/assets/images/hamburger.svg" class="drawer-toggle"  />
			</div>
    <div class="title">
      Acme Corporation
    </div>
  </header>
</template>

<style lang="scss" scoped>
.header {
  position: sticky;
  display: flex;
  align-items: center;
  top: 0;
  height: 2em;
  padding: 15px 20px;
  background-color: #eee;
  z-index: 3;
  .drawer-toggle {
    cursor: pointer;
    .notebook &, .desktop & {
      display: none;
    }
  }
  .title {
    font-size: 1.5em;
    margin-left: 1em;
  }
}
</style>
