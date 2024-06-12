<script setup>
import OdontogramViewer from './components/OdontogramViewer.vue';
</script>

<template>
  <div class="p-4">
    <OdontogramViewer
      :devMode="true"
      title="Odontogram"
      :isPermanent="true"
      notation="fdi"
    />
  </div>
</template>
