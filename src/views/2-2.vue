<template>
  <div class="home">
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
import axios from 'axios'

export default {
  name: 'Axios2-2',
  components: {
  },
  create(){
    // http://localhost:8080/data.json
    axios.get('/data.json').then((res)=>{
      console.log(res)
    })
    axios({
        method: 'get',
        url: '/data.json'
    }).then(res=>{
        console.log(res)
    })
  },
}
</script>