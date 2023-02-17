<script setup lang="ts">
import { onMounted, reactive } from 'vue';
import { devStats } from '../mockData/git-stats';

let devData = reactive({});

onMounted(() => {
  devData = transformContributions(devStats as IDevStatsData);
  console.log(devData);
});

interface IDevStatsData {
  commits: {
    [key: string]: {
      [key: string]: number;
    };
  };
}

const transformContributions = (data: IDevStatsData) => {
  return Object.entries(data.commits).map(([key, element]) => {
    const date = new Date(key);
    const contributionCount = Object.values(element).reduce(
      (acc, commitCount) => acc + commitCount,
      0
    );

    return {
      date: date,
      count: contributionCount,
    };
  });
};
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
