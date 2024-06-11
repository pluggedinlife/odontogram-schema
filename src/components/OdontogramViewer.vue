<script setup>
import { onRenderTracked } from 'vue';
import teethList from '../constants/teethList';

defineProps({
  devMode: Boolean,
  title: String,
  isPermanent: Boolean,
});

let upperArch = [];
let lowerArch = [];

onRenderTracked(() => {
  const list = Object.assign({}, teethList);
  resetLocalData();
  list.permanent.forEach((item) => {
    if (item.id <= 15) {
      upperArch.push(item);
    } else {
      lowerArch.push(item);
    }
  });
});

// LOCAL UTILS
function resetLocalData() {
  upperArch = [];
  lowerArch = [];
}
</script>

<template>
  <div class="flex flex-col" :class="devMode ? 'bg-blue-100 ' : ''">
    <div class="m-5 font-semibold">
      <span>{{ title }}</span>
    </div>

    <div class="flex flex-col min-w-[800px]">
      <!-- UPPER ARCH -->
      <div class="flex flex-row-reverse">
        <div
          class="border border-gray-500 h-40 w-20"
          v-for="(element, index) in upperArch"
          :key="index"
        >
          {{ element.uns }}
        </div>
      </div>

      <div class="border border-b mx-2 border-gray-400 my-4" />

      <!-- LOWER ARCH -->
      <div class="flex">
        <div
          class="border border-gray-500 h-40 w-20"
          v-for="(element, index) in lowerArch"
          :key="index"
        >
          {{ element.uns }}
        </div>
      </div>
    </div>
  </div>
</template>
