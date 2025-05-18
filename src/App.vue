<template>
  <div class="p-4">
    <!-- <OdontogramViewer
      :devMode="false"
      title="Odontogram"
      :isPermanent="true"
      notation="fdi"
    /> -->

    <div class="flex space-x-4">
      <element-schema
        v-for="(element, index) in elementsList"
        :key="index"
        class="border border-gray-500"
        :element="element"
        :isPermanent="true"
        :notation="'uns'"
        :devMode="false"
      >
        <img-1
      /></element-schema>
    </div>
  </div>
</template>

<script setup>
// import OdontogramViewer from './components/OdontogramViewer.vue';
import ElementSchema from './components/ElementSchema.vue';
import Img1 from './components/img/Img1.vue';

const element = {
  id: 0,
  uns: '1',
  fdi: '18',
  roots: [
    {
      id: 0,
      name: '1',
      color: 'red',
    },
    {
      id: 0,
      name: '1',
      color: 'red',
    },
    {
      id: 0,
      name: '1',
      color: 'red',
    },
  ],
  crown: [
    {
      id: 0,
      name: '1',
      color: 'red',
    },
    {
      id: 1,
      name: '2',
      color: 'red',
    },
    {
      id: 2,
      name: '3',
      color: 'red',
    },
    {
      id: 3,
      name: '4',
      color: 'red',
    },
    {
      id: 4,
      name: '5',
      color: 'red',
    },
  ],
};

const elementsList = [
  {
    id: 0,
    uns: '1',
    fdi: '18',
    roots: [
      {
        id: 0,
        name: '1',
        color: 'red',
      },
      // {
      //   id: 0,
      //   name: '2',
      //   color: 'red',
      // },
      // {
      //   id: 0,
      //   name: '3',
      //   color: 'red',
      // },
    ],
    crown: [
      {
        id: 0,
        name: '1',
        color: 'red',
      },
      {
        id: 1,
        name: '2',
        color: 'red',
      },
      {
        id: 2,
        name: '3',
        color: 'red',
      },
      {
        id: 3,
        name: '4',
        color: 'red',
      },
      {
        id: 4,
        name: '5',
        color: 'red',
      },
    ],
  },
  {
    id: 1,
    uns: '2',
    fdi: '17',
    roots: [
      {
        id: 0,
        name: '1',
        color: 'red',
      },
      {
        id: 0,
        name: '2',
        color: 'red',
      },
      // {
      //   id: 0,
      //   name: '3',
      //   color: 'red',
      // },
    ],
    crown: [
      {
        id: 0,
        name: '1',
        color: 'red',
      },
      {
        id: 1,
        name: '2',
        color: 'red',
      },
      {
        id: 2,
        name: '3',
        color: 'red',
      },
      {
        id: 3,
        name: '4',
        color: 'red',
      },
      {
        id: 4,
        name: '5',
        color: 'red',
      },
    ],
  },
  {
    id: 2,
    uns: '3',
    fdi: '16',
    roots: [
      {
        id: 0,
        name: '1',
        color: 'red',
      },
      {
        id: 0,
        name: '2',
        color: 'red',
      },
      {
        id: 0,
        name: '3',
        color: 'red',
      },
    ],
    crown: [
      {
        id: 0,
        name: '1',
        color: 'red',
      },
      {
        id: 1,
        name: '2',
        color: 'red',
      },
      {
        id: 2,
        name: '3',
        color: 'red',
      },
      {
        id: 3,
        name: '4',
        color: 'red',
      },
      {
        id: 4,
        name: '5',
        color: 'red',
      },
    ],
  },
];
</script>
