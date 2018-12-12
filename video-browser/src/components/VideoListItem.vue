<template>
  <li @click="onVideoSelect">
    <img :src="thumbnailUrl" />
    <h4>{{ video.snippet.title }}</h4>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: {
    video: Object
  },
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video)
    }
  },
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url
    }
  }
}
</script>

<style scoped>
  li {
    margin: 5px;
    list-style-type: none;
    display: block;
    clear: both;
  }
  img {
    float: left;
    height: 100%;
  }
  h4 {
    padding: 2px 5px;
  }
</style>