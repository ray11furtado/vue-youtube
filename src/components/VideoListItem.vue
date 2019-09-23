<template>
  <li @click="onVideoSelect" class="list-group-item media">
    <img class="mr3" :src="getThumbnailUrl" />
    <div class="media-body">{{video.snippet.title}}</div>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: {
    video: {
      snippet: {}
    }
  },
  computed: {
    getThumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video);
    }
  }
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
.media-body {
  padding-left: 5px;
}
</style>
