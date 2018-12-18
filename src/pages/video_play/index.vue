<template>
  <div class="container"> 	 
    <video id="videoID" webkit-playsinline="true" x-webkit-airplay="true"  playsinline="true" x5-video-player-type="h5" x5-video-player-fullscreen="true" width="100%" height="100%" preload="auto" poster="" style="object-fit: fill; width:100%; height:100vh;" src="http://www.w3school.com.cn//i/movie.mp4">
 </video>

  </div>
</template>

<style lang="scss">
@import '@/common/scss/style.scss';


</style>

<script>

export default {
  data() {
    return {};
  },

  components: {
  },

  methods: {
  },

  created() {},
  mounted() {
  },
};
</script>
