<template>
<div>
<h1>测试接口</h1>
<input @click="addUser" type="button" v-bind:value="content">
</div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  //接口地址
  public url = "http://www.itokay.cn/api/v1/user";

  //接口需要的参数
  public params:object = {
    "name":"Jon",
    "sex":1,
    "age":8,
    "avator":"http://tx.haiqq.com/uploads/allimg/170506/0G9454641-12.jpg"
  }

  //fetch参数
  protected option:object = {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(this.params)
  }

  //按钮文字
  protected content:string = "调用新增用户接口";

  //事件方法
  public async addUser(){
    let result = await fetch(this.url,this.option);

    result.json().then((data)=>{
      console.log(data);
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
