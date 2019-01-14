<template>
    <ul class="list-group col-md-4">
        <VideoListItem
        v-for="video in videos"
        :video="video"
        :key="video.etag"
        @videoSelect="onvideoSelect"
        >
        '위에서 지정한 video는 v-bind tag의 뒤의 event이다.'
        </VideoListItem>
    </ul>
    
</template>

<script>
import VideoListItem from './VideoListItem';

export default {
  name: 'VideoList',
  components: {
    VideoListItem
  },
  props: ['videos'],
  methods: {
    onvideoSelect(video) {
      this.$emit('videoSelect', video);
    }
  }
};
</script>

<style>

</style>
