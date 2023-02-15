<script setup lang="ts">
import { onMounted, reactive } from 'vue';
import { devStats } from '../mockData/git-stats';

let devData = reactive({});

onMounted(() => {
  devData = devStats;
  console.log(devData);
});
</script>

<template>
  <div>
    <div>Profile Pic</div>
    <div>Location</div>
    <div>Motto</div>
    <div>Current Level</div>
    <div>Contributions calendar</div>
    <div>Achievements</div>
    <div>Main tech stack</div>
  </div>
</template>

<style scoped></style>
