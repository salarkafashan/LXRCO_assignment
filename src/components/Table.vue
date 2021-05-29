<template>
  <div>
     <table class="table table-hover text-start">
        <thead class="table-dark">
          <tr>
            <th scope="col">#</th>
            <th scope="col">Topics</th>
            <th scope="col">Levels</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in items" :key="item.id" scope="row" v-on:click="showDetails(item)">
            <th>{{item.id}}</th>
            <td>{{item.topics.toString().replaceAll(",", " - ")}}</td>
            <td>{{item.levels.toString().replaceAll(",", " - ")}}</td>
          </tr>
        </tbody>
      </table>
  </div>
</template>

<script>
import axios from "axios";


export default {

  name: 'Table',

   mounted () {
    axios.get('https://api.sampleapis.com/codingresources/codingResources')
    .then(response => (this.items = response.data))
  },
  
   data(){
    return{
      items: null
    }
  },

  methods: {
      showDetails: function (item) {
          alert(item.id);
      }
  },
}
</script>


