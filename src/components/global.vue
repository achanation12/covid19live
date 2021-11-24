<template>
  <div class="text-center mt-4">
    <h2>Global<span class="fw-light fs-6">/{{ globalLength }}</span></h2>
  </div>
  <div class="container">
    <input type="text" class="form-control" v-model="searchQuery" placeholder="Cari negara">
    <div v-if="global.length" class="row">
      <div v-for="item in resultQuery" :key="item" class="col-lg-3 col-ms-6 mt-3">
        <div class="card">
          <div class="card-header bg-info bg-gradient text-light">
            {{ item.attributes.Country_Region }}
          </div>
          <div class="card-body">
            Positif
            <h3>{{ Number(item.attributes.Confirmed).toLocaleString() }}</h3>
            Meninggal
            <h3>{{ Number(item.attributes.Deaths).toLocaleString() }}</h3>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
const axios = require('axios');

export default {
  name: 'indoneisa',
  data() {
    return {
      searchQuery: null,
      global: [],
    };
  },
  mounted() {
    axios({
      method: 'post',
      Type: 'json',
      url: 'http://localhost:8080/',
      headers: {
          'Access-Control-Allow-Origin':'*',
          'Content-Type': 'application/json'
        },
      // data: {
      //   categoryid: '6'
      // }
    })
      .then(response => {
        // alert(response.data.Author);
        // console.log(response.data);
        this.global = response.data;
        this.globalLength = response.data.length;
      })
      .catch(error => {
        console.log(error);
    });
  },
  computed: {
    resultQuery(){
      if(this.searchQuery){
      return this.global.filter((item)=>{
        return this.searchQuery.toLowerCase().split(' ').every(v => item.attributes.Country_Region.toLowerCase().includes(v))
      })
      }else{
        return this.global;
      }
    }
  }
}
</script>