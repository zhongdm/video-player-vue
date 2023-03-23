<template>
  <div class="video-main">
    <video
      ref="player"
      class="video-containter"
      :src="url"
      :controls="controls"
      @play="onplay"
      @volumechange="onvolumechange"
      @timeupdate="ontimeupdate"
      @pause="onpause"
      @abort="onabort"
    ></video>

    <!-- <button class="play-btn toggle-show"
      :style="{backgroundImage: 'url('+require('../assets/icon/'+ bgAvatar) + ')'}"
      @click="btnClick"></button> -->
  </div>
</template>

<script>

export default {
  name: '@miyazhong/video-player-vue',
  props: {
    url: String
  },
  data() {
    return {
      controls: 'contrtols',
      bgAvatar: 'play.svg'
    }
  },
  mounted() {
    // this.$refs.player && this.$refs.player.focus();
  },
  methods: {
    onvolumechange(args) {
    },
    onplay(args) {
      this.bgAvatar = 'pause.svg';
    },
    onabort(args) {
      this.bgAvatar = 'play.svg';
    },
    onpause(args) {
      this.bgAvatar = 'play.svg';
    },
    ontimeupdate(args) {
    },
    btnClick(evt) {
      const player = this.$refs.player;
      if (player.paused) {
        player.play();
        this.bgAvatar = 'pause.svg';
      } else {
        player.pause();
        this.bgAvatar = 'play.svg';
      }
    }
  }
}
</script>

<style>
.video-main {
  position: relative;
  /* width: 500px; */
  /* height: 400px; */
  margin: 0 auto;
  background: #000;
}
.video-main:hover {
  cursor: pointer;
}
.video-containter {
  width: 100%;
  height: 100%;
}
.play-btn {
  position: absolute;
  left: calc(50% - 20px);
  top: calc(50% - 20px);
  width: 40px;
  height: 40px;
  border: none;
  background-color: transparent;
  background-repeat: no-repeat;
  background-size: contain;
}
.video-main .toggle-show, .toggle-show {
  display: none;
  cursor: none;
}
.video-main:hover .toggle-show, .toggle-show:hover{
  display: block;
  cursor: pointer;
  box-shadow: 0 0 8px 2px #ffe6e6;
  border-radius:8px;
}
</style>
