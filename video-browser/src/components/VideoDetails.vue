<template>
  <div class="details">
  <div class="video-player">
    <iframe :src="videoUrl"/>
  </div>
    <h3>{{video.snippet.title}}</h3>
    <p>{{video.snippet.description}}</p>
  </div>
</template>

<script>
export default {
  name: 'VideoDetails',
  props: {
    video: Object
  },
  computed: {
    videoUrl() {
      return 'https://www.youtube.com/embed/' + this.video.id.videoId
    }
  }
}
</script>

<style scoped>
.details {
  margin: 10px 0;
  padding: 10px 0;
}
h3 {
  color: rgb(58, 58, 58);
}
p {
  color: #444;
}
.video-player {
  display: flex;
}

iframe {
  flex: 1;
  min-height: 350px;
}
</style>
