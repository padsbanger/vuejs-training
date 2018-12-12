<template>
  <div>
    <SearchBar @termChange="onTermChange"/>
    <VideoDetails v-if="this.selectedVideo" :video="this.selectedVideo"/>
    <VideoList :videos="this.videos" :loading="this.loading" @videoSelect="onVideoSelect"/>
  </div>
</template>

<script>
  import SearchBar from './components/SearchBar';
  import VideoList from './components/VideoList';
  import VideoDetails from './components/VideoDetails'
  import axios from 'axios';

  const API_KEY = 'AIzaSyDUeLJXCAsdtJ8iCWq49t6e_sJJzGgbWdQ';

  export default {
    name: 'App',
    components: {
      SearchBar, VideoList, VideoDetails
    },
    data() {
      return {
        videos: [],
        loading: false,
        selectedVideo: null,
      }
    },
    methods: {
      onTermChange(value) {
        this.loading = true;
        axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: value,
          }
        }).then((data) => {
          setTimeout(() => {
            this.loading = false;
            this.videos = data.data.items;
          }, 300)
        })
      },
      onVideoSelect(video) {
        this.selectedVideo = video;
      }
    }
  }
</script>
