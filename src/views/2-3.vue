<template>
  <div class="home">
    <h1>This a 2-3 view</h1>
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
  name: "axios2-3",
  components: {},
  create() {
    // axios.all() axios.spread()
    axios.all(
        [
            axios.get('/data.sjon'),
            axios.get('/city.json')
        ]
    ).then(
        axios.spread((dataRes, cityRes)=>{
            console.log(dataRes, cityRes)
        })
    )
  }
};
</script>