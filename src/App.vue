<template>
  <div id="app">
    <evil-ad>
      우와 정말 놀라운 광고!<br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      Lorem, ipsum dolor sit amet consectetur adipisicing elit.<br>
      Voluptatibus facere quam nulla repellendus unde obcaecati,<br>
      quidem laudantium error asperiores rerum,<br>
      iusto est dignissimos quia eveniet consectetur praesentium cumque repudiandae natus?
    </evil-ad>
  </div>
</template>

<script>
import EvilAd from './components/EvilAd.vue'

export default {
  name: 'app',
  components: { EvilAd }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}

.evil-ad {
  position: absolute;
  top: 100px; left: 100px;
}

.evil-ad .ad-content {
  padding: 5px;
}
</style>
