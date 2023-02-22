<template>
  <div>
    <MyCameraComponent ref="cameraComponent" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import MyCameraComponent from './MyCameraComponent.vue';

export default defineComponent({
  components: {
    MyCameraComponent,
  },
  mounted() {
    this.updateCamera();
  },
  methods: {
    updateCamera() {
      requestAnimationFrame(() => {
        const cameraComponent = this.$refs.cameraComponent as typeof MyCameraComponent;
        const videoElement = cameraComponent.$refs.videoElement as HTMLVideoElement;

        if (!videoElement.paused && !videoElement.ended) {
          cameraComponent.updateVideo();
        }

        this.updateCamera();
      });
    },
  },
});
</script>
