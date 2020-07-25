<template>
  <div class="home">
    <h1>This a 3-3 view</h1>
  </div>
</template>

<script>
// 拦截器：在请求或响应被处理前拦截它们
// 请求拦截器，响应拦截器
import axios from "axios";

export default {
  name: "axios3-3",
  components: {},
  create() {
    //请求拦截器
    axios.interceptors.request.use(
      config => {
        // 在发送请求前做些什么
        return config;
      },
      err => {
        //在请求错误的时候做些什么
        return Promise.reject(err);
      }
    );
    axios.interceptors.response.use(
      res => {
        // 请求成功对响应数据作处理
        return res;
      },
      err => {
        // 响应错误做些什么
        return Promise.reject(err);
      }
    );
    //  取消拦截器（了解）
    let interceptors = axios.interceptors.request.use(config => {
      config.headers = {
        auth: true
      };
      return config;
    });
    axios.interceptors.request.eject(interceptors);

    //🌰 登录状态(token:''), 需要登录的接口
    let instance = axios.create({});
    instance.interceptors.request.use(config => {
      config.headers.token = "";
      return config;
    });
    // 不需要登录的接口
    let newInstance = axios.create({});

    // 移动端开发
    let instance_phone = axios.create({});
    instance_phone.interceptors.request.use(config => {
      $("#model").show();
      return config;
    });
    instance_phone.interceptors.response.use(res => {
      $("model").hide();
      return res;
    });
  }
};
</script>