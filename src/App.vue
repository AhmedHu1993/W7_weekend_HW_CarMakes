<template>
  <div id="app">
    <h1>Car Makes</h1>
    <div id="display">
      <div id="makes-list">
        <h2>All Makes</h2>
       <makes-list :makes="carMakes"></makes-list>
      </div>
      <div id="fav-list">
        <h2>Favourite Makes</h2>
        <makes-fav :makes="favMakes"></makes-fav>
      </div>
    </div>
  </div>
</template>

<script>
import MakesList from "./components/MakesList"
import MakesFav from "./components/MakesFav"
import { eventBus } from "./main"

export default {
  
  data() {
    return {
      carMakes:[],
      selectedMake: null,
      favMakes: []
    }
  },
  components: {
    "makes-list": MakesList,
    "makes-fav": MakesFav
  },
  mounted() {
    fetch("https://parallelum.com.br/fipe/api/v1/carros/marcas")
    .then(res => res.json())
    .then(makesData => this.carMakes = makesData)
    
    eventBus.$on('fav-make', (make) =>{
      if (this.favMakes.includes(make) === false) {
        this.favMakes.push(make);
      }
      
    })
  }
}
</script>

<style>
#app {
  background-image: url('../../cars.jpg');
  background-repeat: no-repeat;
  background-size: auto;
  height: 1000px;
  margin: 0;
  color: white;
}
#display {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
</style>