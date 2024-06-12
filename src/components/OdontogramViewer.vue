<script setup>
import { onRenderTracked } from 'vue';
import teethList from '../constants/teethList';
import ElementSchema from './ElementSchema.vue';

defineProps({
  devMode: Boolean,
  title: String,
  isPermanent: Boolean,
  notation: String, // uns / fdi
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
  <div
    class="flex flex-col border border-gray-500 rounded-lg overflow-auto"
    :class="devMode ? 'bg-blue-100 ' : ''"
  >
    <div class="m-4 font-semibold" :class="devMode ? 'bg-orange-100 ' : ''">
      <span>{{ title }}</span>
    </div>

    <div class="flex flex-col items-center min-w-[1200px]">
      <!-- UPPER ARCH -->
      <div>
        <div class="w-full flex justify-between">
          <span>LX</span>
          <span>RX</span>
        </div>

        <div class="flex flex-row-reverse">
          <ElementSchema
            class="border border-gray-500 h-40 w-20"
            v-for="(element, index) in upperArch"
            :key="index"
            :element="element"
            :isPermanent="isPermanent"
            :notation="notation"
            :devMode="devMode"
          />
        </div>
      </div>

      <div class="border border-b mx-2 border-gray-400 my-4" />

      <!-- LOWER ARCH -->
      <div>
        <div class="flex">
          <ElementSchema
            class="border border-gray-500 h-40 w-20"
            v-for="(element, index) in lowerArch"
            :key="index"
            :element="element"
            :isPermanent="isPermanent"
            :notation="notation"
            :devMode="devMode"
            :isReverse="true"
          />
        </div>

        <div class="w-full flex justify-between">
          <span>LX</span>
          <span>RX</span>
        </div>
      </div>
    </div>
  </div>
</template>
