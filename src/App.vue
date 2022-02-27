<script setup lang="ts">
import JobBoard from "./components/JobBoard.vue";
import data from "./assets/data.json";
//getting data from the JSON file
const jobs = data;

let jobsArray: any = [];

//adding data from the JSON to the jobs array
for (const job of jobs) {
  jobsArray.push(job);
}

//filtering

function filteringData(clickedItem: string) {
  //CREATING TOP FILTER BAR
  const jobDivElements = document.querySelectorAll("#jobDiv");
  const filteredBoxText = document.createElement("p");
  const closeFilterIcon = document.createElement("button");

  filteredBoxText.textContent = clickedItem;

  filteredBoxText.className =
    "filter-text-box text-teal-500 bg-teal-100 font-bold px-2 rounded m-2 flex gap-2 items-center";
  const filterBox = document.querySelector("#filterBox");
  if (filterBox?.textContent?.includes(clickedItem)) {
    return;
  }

  filterBox?.append(filteredBoxText);

  //functionality
  const filters = document.querySelectorAll(".filter-text-box");
  for (const filter of filters) {
    for (const jobDiv of jobDivElements) {
      if (!jobDiv.textContent.includes(filter.textContent)) {
        jobDiv.style.display = "none";
      }
    }
  }


//checking if the Clear ALL button was already existed or not
  if (!filterBox.textContent.includes("CLEAR")) {
    const clearAllButton = document.createElement("button");
    clearAllButton.textContent = "CLEAR";
    clearAllButton.className =
      "clear-all-button text-teal-500 hover:underline transition absolute right-14";
// adding clear All Button 
    filterBox.append(clearAllButton);
    clearAllButton.addEventListener("click", () => {
      clearAllButton.remove();
      for (const jobDiv of jobDivElements) {
        jobDiv.style.display = "flex";

        const filters = document.querySelectorAll(".filter-text-box");

        for (const filter of filters) {
          // clearAllButton.remove()
          filter.remove();
        }
      }
    });
  }
}
</script>

<template>
  <header class="bg-teal-500 mb-12">
    <img
      class="hidden md:block w-full"
      src="/images/bg-header-desktop.svg"
      alt=""
    />
    <img
      class="md:hidden w-full h-48"
      src="/images/bg-header-mobile.svg"
      alt=""
    />
  </header>

  <!-- filter box -->
  <div
    id="filterBox"
    class="flex md:flex-row items-center bg-white shadow-md mx-10 rounded flex-wrap items-center"
  ></div>

  <!-- all jobs go here -->
  <JobBoard
    v-for="job in jobsArray"
    :companyName="job.company"
    :logoImg="job.logo"
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
    @filteringData="filteringData"
  >
  </JobBoard>
</template>
