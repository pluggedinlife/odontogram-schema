<template>
  <div
    class="flex items-center justify-center p-2 space-y-2 h-full w-24 relative border-2 border-gray-300 rounded-lg shadow-md"
    :class="computedClass"
  >
    <slot />

    <div class="absolute flex flex-col h-full w-full">
      <!-- Title section -->
      <div
        class="text-gray-400 text-center"
        :class="devMode ? 'bg-teal-100 ' : ''"
      >
        {{
          element != undefined && notation != undefined
            ? element[notation]
            : '-'
        }}
      </div>

      <!-- Root -->
      <div
        class="flex flex-1 px-2 justify-center"
        :class="devMode ? 'bg-purple-300 ' : ''"
      >
        <div
          v-if="isRootAvailable('1')"
          class="w-1/3 text-center cursor-pointer hover:bg-red-200 border rounded-lg"
        >
          {{ props.element.roots[0].name }}
        </div>
        <div
          v-if="isRootAvailable('2')"
          class="w-1/3 text-center cursor-pointer hover:bg-red-200 border rounded-lg"
        >
          {{ props.element.roots[1].name }}
        </div>
        <div
          v-if="isRootAvailable('3')"
          class="w-1/3 text-center cursor-pointer hover:bg-red-200 border rounded-lg"
        >
          {{ props.element.roots[2].name }}
        </div>
      </div>

      <!-- Crown -->
      <div
        class="grid grid-cols-3 grid-rows-3 text-center gap-2 pb-2"
        :class="devMode ? 'bg-gray-300 ' : ''"
      >
        <div class="col-span-1" />
        <div
          v-if="element.roots"
          class="col-span-1 cursor-pointer border rounded-lg hover:bg-red-200"
        >
          {{ element.crown[0].name }}
        </div>
        <div class="col-span-1" />

        <div
          class="col-span-1 cursor-pointer border rounded-lg hover:bg-red-200"
        >
          {{ element.crown[3].name }}
        </div>
        <div
          class="col-span-1 cursor-pointer border rounded-lg hover:bg-red-200"
        >
          {{ element.crown[4].name }}
        </div>
        <div
          class="col-span-1 cursor-pointer border rounded-lg hover:bg-red-200"
        >
          {{ element.crown[1].name }}
        </div>

        <div class="col-span-1" />
        <div
          class="col-span-1 cursor-pointer border rounded-lg hover:bg-red-200"
        >
          {{ element.crown[2].name }}
        </div>
        <div class="col-span-1" />
      </div>
    </div>
  </div>
</template>

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
function isRootAvailable(name) {
  let result = false;
  if (props.element != undefined && (name != undefined || name != '')) {
    const found = props.element.roots.find((item) => item.name == name);
    if (found != undefined) result = true;
  }
  return result;
}
</script>
