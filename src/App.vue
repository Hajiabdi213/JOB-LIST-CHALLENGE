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
  const jobDiv = document.querySelectorAll("#jobDiv");
  const filteredBoxText = document.createElement("p");
  const closeFilterIcon = document.createElement("button");
  const clearAllButton=document.createElement("button")
  // clearAllButton.className="clear-all-button text-teal-500 hover:underline transition absolute right-14"

  // clearAllButton.textContent="clear"
  closeFilterIcon.textContent = "X";
  closeFilterIcon.className =
    "close-filter-icon text-white font-bold bg-teal-500 p-2 -mr-2 rounded-r";
  filteredBoxText.textContent = clickedItem;

  filteredBoxText.className =
    "text-teal-500 bg-teal-100 font-bold px-2 rounded m-2 flex gap-2 items-center";
  const filterBox = document.querySelector("#filterBox");
  if (filterBox?.textContent?.includes(clickedItem)) {
    return;
  }
  

  filteredBoxText.append(closeFilterIcon);
  filterBox?.append(filteredBoxText);

  jobDiv.forEach((div) => {
    // console.log(div)

    //removing unwanted Jobs to filter
    if (!div.textContent.includes(clickedItem)) {
      div.classList.add("remove-jobs");

    }

    
    //close filter functionality

    
    closeFilterIcon.addEventListener("click", (e) => {
      
      div.classList.remove("remove-jobs");
     

       const closeFilterIconButton=document.querySelectorAll('.close-filter-icon')
 
   
      
      closeFilterIcon.parentElement?.remove();
      return
    });
  });
}


</script>

<template>
  <header class="bg-teal-500 mb-12">
    <img class="hidden md:block w-full" src="/images/bg-header-desktop.svg" alt="" />
    <img class=" md:hidden w-full h-48" src="/images/bg-header-mobile.svg" alt="" />
  </header>

  <!-- filter box -->
  <div
    id="filterBox"
    class="flex md:flex-row items-center bg-white shadow-md mx-10 rounded flex-wrap"
  >
  
  
  </div>

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
    <!-- <img src="./assets/images/insure.svg" alt=""> -->
    <!-- {{job.company}} -->
  </JobBoard>
</template>
