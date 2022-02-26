<script setup lang="ts">
import JobBoard from "./components/JobBoard.vue";
import data from "./assets/data.json";
import { useTransitionState } from "@vue/runtime-core";
//getting data from the JSON file
const jobs = data;

let jobsArray = [];

//adding data from the JSON to the jobs array
for (const job of jobs) {
  jobsArray.push(job);
}

console.log(jobsArray);

// const jobArray= []
// // console.log(jobs)
// for (const job of jobs) {
//     jobArray.push(job)
// }
console.log("The Job ");
</script>

<template>
<header class="bg-teal-500 mb-12">
  <img src="/images/bg-header-desktop.svg" alt="">
</header>

<!-- all jobs goes here -->
  <JobBoard
    v-for="job in jobsArray"
    :companyName="job.company"
    :logoImg="job.logo"
    :jobPostion="job.position"
    :postedTime="job.postedAt"
    :location="job.location"
    :contract="job.contract"
    :jobPosition="job.position"
    :languages="job.languages"
    :tools="job.tools"
    :level="job.level"
    :role="job.role"
    :isNew="job.isNew"
    :featured="job.featured"
  >
    <!-- <img src="./assets/images/insure.svg" alt=""> -->
    <!-- {{job.company}} -->
  </JobBoard>
</template>
