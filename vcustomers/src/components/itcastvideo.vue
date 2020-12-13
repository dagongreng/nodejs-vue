<template>
  <div class="video container">
    <video>
      <source :src="src" />
    </video>
    <div class="control">
    </div>
  </div>
</template>

<script>
import itcastvideo from './itcastvideo'
export default {
  itcastvideo:{
    itcastvideo
  },
  props:['src']
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  padding: 0;
  margin: 0;
}
</style>
