<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- 下の行を修正 -->
    <HelloWorld v-bind:msg="message"/>
  </div>
</template>
 
<script>
import HelloWorld from './components/HelloWorld.vue'
 
export default {
  name: 'App',
  components: {
    HelloWorld
  },
  // ここから追加
  data: function () {
    return {
      message: 'Loading...'
    }
  },
  mounted: function () {
    fetch('https://nfz4hxrfp1.execute-api.ap-northeast-1.amazonaws.com/dev/ping')
    .then(function (res) {
      return res.json()
    })
    .then(function (json) {
      this.message = json.message
    }.bind(this))
    .catch(function (err) {
      console.error(err)
    })
  }
  // ここまで追加
}
</script>
 
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
