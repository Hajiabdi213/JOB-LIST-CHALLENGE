<script setup lang="ts">
// defineProps<{company:string}>();



type allMyProps={
    companyName:string,
    logoImg:string,
    jobPosition:string,
    postedTime:string,
    contract:string,
    location:string,
    languages:string,
    tools:string,
    role:string,
    level:string,
    isNew:boolean,
    featured:boolean



}
 defineProps<allMyProps>();

</script>
<template>

    

<!-- <div className="flex bg-white shadow-md m-4 p-6 rounded" > -->
<div id="jobDiv" v-bind:class = "(featured)?'flex md:flex-row bg-white border-l-4 border-teal-500 border-solid shadow-md mx-10 my-16 p-6 rounded  flex-col':'flex md:flex-row bg-white shadow-md mx-10 my-16 p-6 rounded flex-col  '" >
    <!-- image -->
    <div class="flex items-center">
            <img class=" rounded-3xl w-20   -mt-16 md:m-0" v-bind:src="logoImg" alt="">

    </div>
    <!-- info -->
    <!-- left -->
    <div class="ml-4 flex flex-col justify-between ">
        <h3 class="font-bold  text-teal-500">{{companyName}}
            <span class="bg-teal-500 text-white text-sm m-2 py-1 px-2 rounded-full font-semibold uppercase" v-if="isNew"> New </span>
            <span class="bg-gray-800 text-white text-sm m-2 py-1 px-2 rounded-full  font-semibold uppercase" v-if="featured"> Featured </span>

        </h3>

        <h2 class="font-bold text-xl my-2">{{jobPosition}}</h2>
        <p class="text-gray-700">
            {{postedTime}}
            &#xb7;{{contract}}
           &#xb7; {{location}}
        </p>
    </div>

    <!-- right side -->
    <div class="flex items-center  mt-4 pt-4 border-t border-gray-500 border-solid flex-wrap md:ml-auto md:border-t-0 md:mt-0 md:pt-0">
        <!-- <h1>{{languages}}</h1>
        <h1>{{tools}}</h1> -->
        
        <span @click="$emit('filteringData', role)" class="text-teal-500 bg-teal-100 font-bold p-2 rounded m-2 hover:bg-teal-500 hover:text-white transition duration-300 cursor-pointer">{{role}}</span>
        <span @click="$emit('filteringData', level)" class="text-teal-500 bg-teal-100 font-bold p-2 rounded m-2 hover:text-white transition duration-300 cursor-pointer  hover:bg-teal-500">{{level}}</span>
        <span @click="$emit('filteringData', language)" class="text-teal-500 bg-teal-100 font-bold p-2 rounded m-2 hover:text-white transition duration-300 cursor-pointer hover:bg-teal-500" v-for="language in languages">{{language}}</span>
        <span @click="$emit('filteringData',tool)" class="text-teal-500 bg-teal-100 font-bold p-2 rounded m-2 hover:text-white transition duration-300 cursor-pointer  hover:bg-teal-500" v-for="tool in tools">{{tool}}</span>

    </div>
   
</div>
    
</template>

