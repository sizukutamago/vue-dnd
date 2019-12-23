<template>
  <div id="app">
    <div class="box1" id="drag">
      <p draggable="true">drag</p>
    </div>
    <div class="box2" id="drop" @drop="dropElement"></div>
  </div>
</template>

<script>
export default {
  name: 'app',
  mounted () {
     document.getElementById('drag').addEventListener('dragstart', event => {
       event.dataTransfer.setData('text/plain', event.target.textContent);
     });

     const dropElement = document.getElementById('drop');

     dropElement.addEventListener('dragenter', event => {
       event.preventDefault();
     });

    dropElement.addEventListener('dragover',event => {
      event.dataTransfer.dropEffect = 'copy';
      event.preventDefault();
    });
  },
  methods: {
    dropElement(event) {
      event.preventDefault();
      event.target.innerHTML = event.dataTransfer.getData('text/plain');
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  width: 100vw;
  display: flex;
}

p {
  margin: 5px auto;
  width: 90%;
  background-color: white;
  border-radius: 5px;
  min-height: 10vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.box {
  height: 80vh;
  margin: 0 auto;
  width: 20vw;
  border-radius: 5px;
}

.box1 {
  @extend .box;
  background-color: aquamarine;
}

.box2 {
  @extend .box;
  background-color: gold;
}
</style>
