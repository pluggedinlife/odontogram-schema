<script setup>
import { computed, onRenderTracked } from 'vue';

const props = defineProps({
  devMode: Boolean,
  notation: String, // uns, fdi
  isPermanent: Boolean,
  element: Object,
  isReverse: Boolean,
});

onRenderTracked(() => {});

const computedClass = computed(() => {
  let result = '';
  if (props.devMode) {
    result += 'bg-purple-100 ';
  }
  if (props.isReverse) {
    result += 'flex-col-reverse ';
  } else {
    result += 'flex-col ';
  }
  return result;
});
</script>

<template>
  <div class="flex p-2" :class="computedClass">
    <!-- Title section -->
    <div
      class="text-gray-400 text-center"
      :class="devMode ? 'bg-teal-100 ' : ''"
    >
      {{
        element != undefined && notation != undefined ? element[notation] : '-'
      }}
    </div>

    <!-- Root -->
    <div class="flex flex-1" :class="devMode ? 'bg-purple-300 ' : ''">
      <div
        class="flex-1 text-center cursor-pointer hover:bg-red-200 border rounded-lg"
        v-for="(root, index) in element.roots"
        :key="index"
      >
        {{ root.name }}
      </div>
    </div>

    <!-- Crown -->
    <div
      class="grid grid-cols-3 grid-rows-3 text-centerp h-1/3"
      :class="devMode ? 'bg-gray-300 ' : ''"
    >
      <div class="col-span-1" />
      <div class="col-span-1 cursor-pointer border rounded-lg hover:bg-red-200">
        {{ element.crown[0].name }}
      </div>
      <div class="col-span-1" />

      <div class="col-span-1 cursor-pointer border rounded-lg hover:bg-red-200">
        {{ element.crown[3].name }}
      </div>
      <div class="col-span-1 cursor-pointer border rounded-lg hover:bg-red-200">
        {{ element.crown[4].name }}
      </div>
      <div class="col-span-1 cursor-pointer border rounded-lg hover:bg-red-200">
        {{ element.crown[1].name }}
      </div>

      <div class="col-span-1" />
      <div class="col-span-1 cursor-pointer border rounded-lg hover:bg-red-200">
        {{ element.crown[2].name }}
      </div>
      <div class="col-span-1" />
    </div>
  </div>
</template>
