<template>
  <div class="home">
    <h1>This a 2-2 view</h1>
  </div>
</template>

<script>
/**
 * axios请求方法：get, post, put, patch, delete
 *
 * get: 获取数据
 * post: 提交数据
 * put: 更新数据（所有数据都推送到后端
 * patch: 更新数据（只提交修改的数据推送到后端
 * delete: 删除数据
 */
import axios from "axios";

export default {
  name: "Axios2-2",
  components: {},
  create() {
    // http://localhost:8080/data.json
    axios.get("/data.json").then(res => {
      console.log(res);
    });
    axios({
      method: "get",
      url: "/data.json"
    }).then(res => {
      console.log(res);
    });
    // post
    // form-data 表单提交(图片上传，文件上传)
    // application/json
    let data = {
      id: 12
    };
    axios.post("/post", data).then(res => {
      console.log(res);
    });
    axios({
      method: "post",
      url: "/post",
      data: data
    }).then(res => {
      console.log(res);
    });
    // form-data请求
    let formData = new FormData();
    for (let key in data) {
      formData.append(key, data[key]);
    }
    axios.post("/post", formData).then(res => {
      console.log(res);
    });
  }
};
</script>