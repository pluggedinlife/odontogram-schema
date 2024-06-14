<script setup>
import OdontogramViewer from './components/OdontogramViewer.vue';
import ElementSchema from './components/ElementSchema.vue';

const element = {
  id: 0,
  uns: '1',
  fdi: '18',
  roots: [
    {
      id: 0,
      name: '1',
    },
    {
      id: 0,
      name: '1',
    },
    {
      id: 0,
      name: '1',
    },
  ],
  crown: [
    {
      id: 0,
      name: '1',
    },
    {
      id: 1,
      name: '2',
    },
    {
      id: 2,
      name: '3',
    },
    {
      id: 3,
      name: '4',
    },
    {
      id: 4,
      name: '5',
    },
  ],
};
</script>

<template>
  <div class="p-4">
    <OdontogramViewer
      :devMode="true"
      title="Odontogram"
      :isPermanent="true"
      notation="fdi"
    />
    <!-- <ElementSchema
      class="border border-gray-500 h-80 w-60"
      :element="element"
      :isPermanent="true"
      :notation="uns"
      :devMode="true"
    /> -->
  </div>
</template>
