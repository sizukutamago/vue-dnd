<template>
  <div id="app">
    <div class="box" id="dragstart">
      <p draggable="true">drag</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  mounted () {
    document.getElementById('dragstart').addEventListener('drag', function () {
      console.log('drag');
    });
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.box {
  height: 10vh;
  width: 10vw;
  margin: 0 auto;
  background-color: aquamarine;
}
</style>
