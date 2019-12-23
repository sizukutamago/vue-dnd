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
       event.dataTransfer.setData('text/plain', event.target.innerText);
     });

    document.getElementById('drop').addEventListener('dragover',event => {
      event.preventDefault();
      event.dataTransfer.dropEffect = 'move';
    });
  },
  methods: {
    dropElement(event) {
      event.preventDefault();
      let element = document.createElement('p');
      element.innerText = event.dataTransfer.getData('text/plain');
      event.target.appendChild(element);
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
