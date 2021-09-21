<template>
<div id="app">
  <div class="general"> Shuffle and sort </div>
  <div class="container">
    <div class="cube_container">
      <div v-for="(cube, index) in cubes" :key="`${cube}_${componentKey}`" class="cube" :class="`cube_${index}`">
        <span class="numbers">{{ cube }}</span>
      </div> 
    </div>
    <div class="btn_container">
      <button class="btn" @click="shuffleCubes()">SHUFFLE</button>
      <button class="btn" @click="sortCubes()">SORT</button>
    </div>
  </div>
  <div class="general"> Shuffle and sort by Sowmya </div>
</div>
</template>

<script>
import Vue from 'vue';
export default {
  name: 'app',
  data () {
    return {
      cubes: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      componentKey: 0,
    }
  },
  methods: {
    sortCubes() {
      this.cubes = this.cubes.sort();
      this.forceRerender();
    },
    shuffleCubes() {
      for (let i = this.cubes.length - 1; i > 0; i--) {
        let j = Math.floor(Math.random() * (i + 1)); // random index from 0 to i
        [this.cubes[i], this.cubes[j]] = [this.cubes[j], this.cubes[i]];
      }
      this.forceRerender();
    },
    forceRerender() {
      this.componentKey += 1;
    }
  },
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #efefef;
  padding: 1em;
}

.general {
  margin: 1em;
}

.cube_container {
  height: 300px;
  width: 300px;
  display: inline-flex;
  flex-wrap: wrap;
}

.container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-content: space-around;
  justify-content: space-around;
}
.cube {
    height: 100px;
    width: 100px;
    display: flex;
    color: white;
    background-color: #efefef;
    align-items: center;
    justify-content: center;
}

.numbers {
  font-weight: 500;
  font-size: xxx-large;
}

.btn {
  padding: 0.5em;
  border-radius: 5px;
  border: transparent;
  background: #6f98a8;
  box-shadow: 0px 5px #2b8ead;
  color: white;
  width: 100%;
  height: 10%;
  cursor: pointer;
  margin: 1em;
}

.cube_0 {
  background-color: #6f98a8;
}

.cube_1 {
  background-color: #2b8ead;
}

.cube_2 {
  background-color: #2f454e;
}

.cube_3 {
  background-color: #2b8ead;
}

.cube_4 {
  background-color: #2f454e;
}

.cube_5 {
  background-color: #bfbfbf;
}

.cube_6 {
  background-color: #bfbfbf;
}

.cube_7 {
  background-color: #6f98a8;
}

.cube_8 {
  background-color: #2f454e;
}

@media only screen and (max-width: 375px) {
  #app {
    background-color: #FFFFFF;
  }

  .btn {
    width: 40%;
    margin: 1em 0.2em;
  }

  .cube {
    color: #000000;
    background-color: #efefef;
    width: 100%;
    height: 15%;
    margin-bottom: 0.5em;
  }

  .container { 
    display: flex;
    flex-direction: column-reverse;
    flex-wrap: wrap;
    align-content: space-around;
    justify-content: space-around;
  }

  .cube_container {
    height: 100%;
  }

  .numbers {
    font-weight: 300;
    font-size: x-large;
  }

.cube_0 {
  border-left: 5px solid #6f98a8;
}

.cube_1 {
  border-left: 5px solid #2b8ead;
}

.cube_2 {
  border-left: 5px solid #2f454e;
}

.cube_3 {
  border-left: 5px solid #2b8ead;
}

.cube_4 {
  border-left: 5px solid #2f454e;
}

.cube_5 {
  border-left: 5px solid #bfbfbf;
}

.cube_6 {
  border-left: 5px solid #bfbfbf;
}

.cube_7 {
  border-left: 5px solid #6f98a8;
}

.cube_8 {
  border-left: 5px solid #2f454e;
}
}
</style>
