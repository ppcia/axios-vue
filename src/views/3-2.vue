<template>
  <div class="home">
    <h1>This a 3-2 view</h1>
  </div>
</template>

<script>
// axios 配置参数有哪些
import axios from "axios";

export default {
  name: "axios3-2",
  components: {},
  create() {
      axios.create({
          baseURL: 'http://localhost:8080',  //请求的域名，基本地址
          timeout: 1000,                    // 请求超时时长(ms)
          url: '/data.json',                //请求路径
          method: 'get',                    //请求方法
          headers: {
              token: ''
          },                               //请求头
          params: {},                      //请求参数拼接在URL
          data: {},                         //请求参数放在请求体
      })
      // 1.axios全局配置
      axios.defaults.timeout = 1000
      axios.defaults.baseURL = 'http://localhost:8080'
      // 2.axios实例配置
      let instance = axios.create()
      instance.defaults.timeout = 3000
      // 3.axios请求配置
      instance.get('/data.json',{
          timeout: 5000
      })
  }
};
</script>