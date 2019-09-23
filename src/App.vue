<template>
  <div class="container">
    <SearchBar @searchChange="onSearchChange"></SearchBar>
    <div class="row">
      <VideoDetail v-if="videoSelected" :video="videoSelected"></VideoDetail>
      <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';
const API_KEY = '';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: [],
      videoSelected: null
    };
  },
  methods: {
    onSearchChange(searchTerm) {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        })
        .then(res => {
          this.videos = res.data.items;
        });
    },
    onVideoSelect(video) {
      this.videoSelected = video;
    }
  }
};
</script>