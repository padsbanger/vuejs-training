<template>
  <div>
    <ul>
    <VideoListItem
      v-for="video in videos"
      :key="video.etag"
      :video="video"
      v-if="!loading"
      @videoSelect="onVideoSelect"
      />
    </ul>
    <div class="loader" v-if="loading" />
  </div>
</template>

<script>

import VideoListItem from './VideoListItem';

export default {
  name: 'VideoList',
  components: {
    VideoListItem
  },
  props: {
    videos: Array,
    loading: Boolean,
  },
  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video)
    }
  }
}
</script>

<style scoped>
 ul {
  margin: 0;
  padding: 0;
  width: 100%;
  display: flex;
  flex-flow: column;
 }
.loader {
  border: 4px solid #f3f3f3; /* Light grey */
  border-top: 4px solid #4adb34; /* Blue */
  border-radius: 50%;
  width: 40px;
  height: 40px;
  animation: spin 2s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>
