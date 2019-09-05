<template >
  <div id="app">
      <div id="box">
        <input type="text" id="information" v-model="msg">
        <button @click="sign">sign</button>
        <div id="show"></div>
      </div>
  </div>
</template>

<style lang="scss">
#box{
        width:600px;
        height:400px;
        border:1px solid #eee;
        margin:50px auto;
        input[type="text"]{
        width:400px;
        height:30px;
        margin:50px;
        display:block;
        }
        button{
            margin-left: 50px;
        }
        #show{
            width:460px;
            margin:0 0 50px 50px;
            height:160px;
            border:1px solid #999;
            padding:20px;
        }
}
</style>
<script>
module.exports = {
   name:"app",
   data(){
     return {
       msg:""
     }
   },
   methods:{
     sign(){
        var web3 = new Web3(Web3.givenProvider || 'ws://some.local-or-remote.node:8546');
        var dataToSign = this.msg;
        web3.eth.sign(web3.fromUtf8(dataToSign), web3.eth.defaultAccount)
        .then(console.log);
      }
   } 
}
</script>