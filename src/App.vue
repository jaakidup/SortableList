<template>
  <div id="app">
    <h1>Movable List</h1>
    <draggable v-model="myArray" group="people" @start="drag=true" @end="drag=false & ending()">
      <transition-group name="flip-list" tag="div">
        <div class="element" v-for="element in myArray" :key="element.id">{{element.name}}</div>
      </transition-group>
    </draggable>

    <p>
      <div v-for="i in myArray" :key="i.id">{{i.name}}</div>
    </p>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld";
import draggable from "vuedraggable";

export default {
  name: "App",
  components: {
    // HelloWorld
    draggable
  },
  methods: {
    ending() {
      console.log(this.myArray);
    }
  },
  data() {
    return {
      image: "assets/wall.jpeg",
      myArray: [
        { id: "1", name: "Jaaki" },
        { id: "2", name: "Brie" },
        { id: "3", name: "Jess" },
        { id: "4", name: "Yvonne" }
      ]
    };
  }
};
</script>

<style>
#app {
  min-width: 300px;
  max-width: 500px;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin-left: auto;
  margin-right: auto;
}

h1 {
  color: grey;
}

.element {
  cursor: grab;
  border-bottom: thin solid rgb(138, 138, 138);
  border-left: 0.5em rgb(3, 137, 199) solid;
  margin: 0.3em;
  padding: 0.5em;

  box-shadow: 0 0 15px 5px silver;

  background: #feffe8;
  background: -moz-linear-gradient(top, #feffe8 0%, #d6dbbf 100%);
  background: -webkit-linear-gradient(top, #feffe8 0%, #d6dbbf 100%);
  background: linear-gradient(to bottom, #feffe8 0%, #d6dbbf 100%);
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#feffe8', endColorstr='#d6dbbf',GradientType=0 );

  font-size: 1.3em;
}

.flip-list-move {
  transition: transform 0.5s;
}
</style>
