<script setup>
import OdontogramViewer from './components/OdontogramViewer.vue';

const odontogramTitle = 'Odontogram';
const isPermanent = false;
</script>

<template>
  <OdontogramViewer
    :devMode="true"
    :title="odontogramTitle"
    :isPermanent="isPermanent"
  />
</template>
