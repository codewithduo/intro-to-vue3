<script setup>
import { RouterView } from "vue-router";
</script>
<template>
  <component :is="$route.meta.layout || 'div'">
    <RouterView></RouterView>
  </component>
</template>
