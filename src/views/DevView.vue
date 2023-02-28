<script setup lang="ts">
import { onMounted, reactive, ref } from 'vue';
import { devStats } from '../mockData/git-stats';
import { CalendarHeatmap } from 'vue3-calendar-heatmap';

interface IDevData {
  date: string;
  count: number;
}
[];

let devData = ref([
  {
    date: new Date(),
    count: 0,
  },
]);

onMounted(() => {
  devData.value = transformContributions(devStats);
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
    <calendar-heatmap :values="devData" :end-date="Date.now()" />
    <div>Achievements</div>
    <div>Main tech stack</div>
  </div>
</template>

<style scoped></style>
