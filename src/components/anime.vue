<template>
  <div id="diffy">
      <h1>
        Galaxy View in Your Birth
      </h1>
    <input type="text" v-model="name" />
    <button class="btn btn-warning" @click="searchData()">ENTER</button>
    <div>
      <h2>
        Ex: 1999-10-29
      </h2>
      <h3>
        **note : This is API NASA Your Can see your galaxy in your birthday 
        Let's get it's on !!! Enjoy in my web. 
        
      </h3>

      
    </div>
    <b-card class="card bg-indigo">
      <b-card
        v-for="data in resultData"
        :key="data.date"
        :title="data.title"
        :img-src="data.hdurl"
      >
        <div>{{ data.explanation }}</div>
       
      </b-card>
    </b-card>
     <h5>Copyright by | HARRiE Dev</h5>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      resultData: null,
      name: "",
    };
  },

  methods: {
    searchData() {
      axios
        .get(
          "https://api.nasa.gov/planetary/apod?api_key=PjegsGGK7fmIKaCllSdF7lC4svqoD7mK0CTT24KR&date=" +
            this.name
        )
        .then((response) => {
          this.resultData = response;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style>
#diffy {
  color: black;
  font-weight: 600;
  background: blanchedalmond;
}
</style>