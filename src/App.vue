<script setup lang="ts">
import {ref, Ref} from 'vue';

let localStream: Ref<MediaStream> = ref(new MediaStream());
const videoRef: Ref<HTMLVideoElement | null> = ref(null);

async function startCall() {
    const mediaStream = await navigator.mediaDevices.getUserMedia({
        audio: true,
        video: true
    });
    // TODO loop tracks and add to remote connection
    videoRef.value!.srcObject = mediaStream;
}
</script>

<template>
    <h1>Webrtc</h1>
  <!--Local stream-->
    <video ref="videoRef"></video>
  <!--Remote stream stream-->
    <button type="button" @click="startCall">Start call</button>
</template>

<style scoped>
</style>
