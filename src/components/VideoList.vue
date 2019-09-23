<template>
  <div class="col-md-4">
    <ul class="list-group">
      <VideoListItem
        @videoSelect="handleVideoClicked"
        v-for="video in videos"
        :key="video.etag"
        :video="video"
      ></VideoListItem>
    </ul>
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
    selectedVideo: {}
  },
  methods: {
    handleVideoClicked(video) {
      this.$emit('videoSelect', video);
    }
  }
};
</script>

<style>
</style>