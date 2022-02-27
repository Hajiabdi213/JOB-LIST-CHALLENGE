<script setup lang="ts">
// defineProps<{company:string}>();

type allMyProps = {
  companyName: string;
  logoImg: string;
  jobPosition: string;
  postedTime: string;
  contract: string;
  location: string;
  languages: string;
  tools: string;
  role: string;
  level: string;
  isNew: boolean;
  featured: boolean;
};
defineProps<allMyProps>();
</script>
<template>
  <!-- <div className="flex bg-white shadow-md m-4 p-6 rounded" > -->
  <div
    id="jobDiv"
    v-bind:class="
      featured
        ? 'job-card-featured'
        : 'job-card'
    "
  >
    <!-- image -->
    <!-- left -->
    <div class="flex items-center">
      <img class="company-logo" v-bind:src="logoImg" alt="" />
    </div>
    <!-- info -->
    <div class="ml-4 flex flex-col justify-between">
      <h3 class="font-bold text-teal-500">
        {{ companyName }}
        <span
          class="isNewStyle"
          v-if="isNew"
        >
          New
        </span> 
        <span
          class="isFeaturedStyle"
          v-if="featured"
        >
          Featured
        </span>
      </h3>

      <h2 class="font-bold text-xl my-2">{{ jobPosition }}</h2>
      <p class="text-gray-700">
        {{ postedTime }}
        &#xb7;{{ contract }} &#xb7; {{ location }}
      </p>
    </div>

    <!-- right side -->
    <div
      class="right-side"
    >
      <!-- <h1>{{languages}}</h1>
        <h1>{{tools}}</h1> -->

      <span @click="$emit('filteringData', role)" class="filter-button">{{
        role
      }}</span>
      <span @click="$emit('filteringData', level)" class="filter-button">{{
        level
      }}</span>
      <span
        @click="$emit('filteringData', language)"
        class="filter-button"
        v-for="language in languages"
        >{{ language }}</span
      >
      <span
        @click="$emit('filteringData', tool)"
        class="filter-button"
        v-for="tool in tools"
        >{{ tool }}</span
      >
    </div>
  </div>
</template>
