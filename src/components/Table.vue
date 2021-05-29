<template>
  <div>
    <div class="row mt-5">
        <div class="col-md-3 text-start">
          <Dropdown @update:option="optionUpdate"/>
        </div>
        <div class="col-md-9 text-end">
          <h5>Welcome to my assignment</h5>
        </div>
      </div>
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

      <b-modal id="detail" size="lg" centered title="More Detail :" header-bg-variant="dark" header-text-variant="light" bodyTextVariant="dark" ok-only hide-header-close>

        <span class="fw-bold">Description :</span>
        <p class="my-2">{{description}}</p>

        <span class="fw-bold">Types : </span>
        <p class="my-2">{{types.toString().replaceAll(",", " - ")}}</p>

        <span class="fw-bold">Topics : </span>
        <p class="my-2">{{topics.toString().replaceAll(",", " - ")}}</p>

        <span class="fw-bold">Levels :</span>
        <p class="my-2"> {{levels.toString().replaceAll(",", " - ")}}</p>

        <span class="fw-bold">Url : </span>
        <br>
        <a :href=url>{{url}}</a>
        <br>
      </b-modal>
  </div>
</template>

<script>
import axios from "axios";
import Dropdown from './Dropdown.vue'

export default {

  name: 'Table',
  components: {
    Dropdown,
  },
   mounted () {
    axios.get('https://api.sampleapis.com/codingresources/codingResources')
    .then(response => (this.items = response.data , this.copyItems = response.data))
  },
  
   data(){
    return{
      test:         null,
      items:        null,
      description:  String,
      url:          String,
      types:        Array,
      topics:       Array,
      levels:       Array,
    }
  },

  methods: {
      showDetails: function (item) {
          this.$bvModal.show('detail');
          this.description = item.description;
          this.url = item.url;
          this.types = item.types;
          this.topics = item.topics;
          this.levels = item.levels;
      },
      optionUpdate:function (event)
      {
        var selectedTopics = [];
        var copyItems = this.copyItems;
        copyItems.forEach(function(entry) {
           if(entry.topics.includes(event.target.value))
           {
              selectedTopics.push(entry);
           }
        });
        this.items = selectedTopics; 
      }
  },
}
</script>


