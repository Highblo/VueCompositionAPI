<script setup>
defineProps(["bgColor"]);
</script>

<template>
  <button :style="{ backgroundColor: bgColor }"><slot>No Title</slot></button>
</template>