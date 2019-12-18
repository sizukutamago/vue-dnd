<template>
  <div id="app">
    <div class="box1" id="drag">
      <p draggable="true">drag</p>
    </div>
    <div class="box2" id="drop" @drop="dropElement">
      <p></p>
    </div>
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

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

p {
  margin: auto;
}

.box1 {
  height: 10vh;
  width: 10vw;
  margin: 0 auto;
  background-color: aquamarine;
}

.box2 {
  height: 10vh;
  width: 10vw;
  margin: 0 auto;
  background-color: gold;
}
</style>
