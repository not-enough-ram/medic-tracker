<template>
  <div>
    <video ref="videoElement"></video>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  mounted() {
    this.initCamera();
    this.updateVideo();
  },
  methods: {
    async initCamera() {
      try {
        const stream = await navigator.mediaDevices.getUserMedia({
          video: true,
        });
        this.$refs.videoElement.srcObject = stream;
      } catch (error) {
        console.error(error);
      }
    },
    updateVideo() {
      requestAnimationFrame(() => {
        const videoElement = this.$refs.videoElement as HTMLVideoElement;

        if (!videoElement.paused && !videoElement.ended) {
          this.updateVideo();
        }
      });
    },
  },
});
</script>
