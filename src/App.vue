<template>
  <div>
    <CameraParent />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CameraParent from './components/CameraParent.vue';

export default defineComponent({
  components: {
    CameraParent,
  },
});
</script>
