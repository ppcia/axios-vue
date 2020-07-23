<template>
  <div class="home">
    <h1>This a 3-1 view</h1>
  </div>
</template>

<script>

// axios实例
// 后端借口地址有多个，并且超市时长不一样

import axios from "axios";

export default {
  name: "axios3-1",
  components: {},
  create() {
      let instance = axios.create({
          baseURL: 'http://localhost:8080',
          timeout: 1000
      })
      instance.get('/data.json').then(
          res=>{
              console.log(res)
          }
      )
  }
};
</script>