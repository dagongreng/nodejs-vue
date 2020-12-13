<template>
  <div class="about container">
    <h1 class="page-header">CETCME 波浪艇南海实验</h1>
    <!-- <itcastvideo src='https://media.vued.vanthink.cn/y2mate.com%20-%20Sparkle%20_%20Your%20Name%20AMV_K_7To_y9IAM_240p.mp4'></itcastvideo> -->
    <video    :preload="preload"
              :poster="videoImg" :height="height" :width="width" align="center" :controls="controls"  :autoplay="autoplay">
        <source :src="videoSrc" type="video/mp4">
    </video>
    <!-- <itcastvideo src = require('../../src/assets/2.mp4')></itcastvideo> -->
  </div>
</template>

<script>
import 'animate.css'
import itcastvideo from 'myitcastvideo456'
import video from 'vue-video-player'

export default {
  name: 'about',
  components:{
    itcastvideo,
    video
  },
  data () {
    return {
      // videoSrc: 'https://media.vued.vanthink.cn/y2mate.com%20-%20Sparkle%20_%20Your%20Name%20AMV_K_7To_y9IAM_240p.mp4',
      // videoSrc: '../../src/assets/3.mp4'
      videoSrc: require('../../src/assets/2.mp4'),
      videoImg: '../../src/assets/logo.png',
      playStatus: '',
      muteStatus: '',
      isMute: true,
      isPlay: true,
      width: '1140', // 设置视频播放器的显示宽度（以像素为单位）
      height: '640', // 设置视频播放器的显示高度（以像素为单位）
      preload: 'auto', //  建议浏览器是否应在<video>加载元素后立即开始下载视频数据。
      controls: true, // 确定播放器是否具有用户可以与之交互的控件。没有控件，启动视频播放的唯一方法是使用autoplay属性或通过Player API。
      autoplay: ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  /* padding: 0;
  margin: 0; */
}
</style>
