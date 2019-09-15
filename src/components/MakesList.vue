<template>
  <div id="list">
      <table>
      <tr>
          <th>Make name</th>
          <th></th>
      </tr>
      <tr v-for="(make, index) in makes" :make='make' :key='index'>
          <td>{{make.nome}}</td>
          <td v-on:click="handleClick(make)" style="cursor:pointer;"> &#11088;</td>
      </tr>
      </table>
  </div>
</template>

<script>
import {eventBus} from '../main'

export default {
    name:'makes-list',
    props: ['makes'],
    methods: {
        handleClick (make){
            eventBus.$emit('fav-make', make)
        }
    }

}
</script>

<style scoped>
#list {
    height: 400px;
    overflow: auto;
    border: 1px solid black;
}
td {
    margin: 0px;
    padding: 0;
}
</style>