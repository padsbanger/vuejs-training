<template>
  <div>
    <SearchBar @termChange="onTermChange"/>
    <VideoList />
  </div>
</template>

<script>
  import SearchBar from './components/SearchBar';
  import VideoList from './components/VideoList';
  import axios from 'axios';

  const API_KEY = 'AIzaSyDUeLJXCAsdtJ8iCWq49t6e_sJJzGgbWdQ';

  export default {
    name: 'App',
    components: {
      SearchBar, VideoList
    },
    methods: {
      onTermChange(value) {
        axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: value,
          }
        }).then((data) => {
          console.log(data)
        })
      }
    }
  }
</script>
