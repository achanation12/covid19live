<template>
  <div class="text-center">
    <h2>{{ indonesia.name }}</h2>
  </div>
  <div class="container">
    <div class="row">
      <div class="col-lg mt-1">
        <div class="card">
          <div class="card-header bg-danger text-light bg-gradient">
            Positif
          </div>
          <div class="card-body">
            <h1>{{ indonesia.positif }}<span class="fw-light fs-6">/orang</span></h1>
            
          </div>
        </div>
      </div>
      <div class="col-lg mt-1">
        <div class="card">
          <div class="card-header bg-warning text-light bg-gradient">
            Dirawat
          </div>
          <div class="card-body">
            <h1>{{ indonesia.dirawat }}<span class="fw-light fs-6">/orang</span></h1>
          </div>
        </div>
      </div>
      <div class="col-lg mt-1">
        <div class="card">
          <div class="card-header bg-dark text-light bg-gradient">
            Meninggal
          </div>
          <div class="card-body">
            <h1>{{ indonesia.meninggal }}<span class="fw-light fs-6">/orang</span></h1>
          </div>
        </div>
      </div>
      <div class="col-lg mt-1">
        <div class="card">
          <div class="card-header bg-success text-light bg-gradient">
            Sembuh
          </div>
          <div class="card-body">
            <h1>{{ indonesia.sembuh }}<span class="fw-light fs-6">/orang</span></h1>
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
      indonesia: [],
    };
  },
  mounted() {
    axios({
      method: 'post',
      url: 'http://localhost:8080/indonesia/',
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
        // console.log(response);
        this.indonesia = response.data[0];
      })
      .catch(error => {
        console.log(error);
    });
  }
}
</script>