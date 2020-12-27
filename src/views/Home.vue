<template>
  <div class="flex">
    <div class="left">
      <SideNavi />
    </div>
    <div class="right">
      <div class="title">
        <p>ホーム</p>
      </div>
      <Message />
    </div>
  </div>
</template>

<script>
import SideNavi from "../components/SideNavi";
import Message from "../components/Message";
export default {
  data(){
    return{
      shares:[{name:"taro", like: 1, share:"初めまして"}]
    };
  },
  components:{
    SideNavi,
    Message
  }
}
</script>

<style scoped>
.left{
  width: 20%;
  height: 100vh;
}
.logo{
  width: 150px;
  cursor: pointer;
}
.flex{
  display: flex;
}
.title {
  border-bottom: 1px solid white;
  border-left: 1px solid white;
  padding: 15px;
}
.title p{
  font-size: 20px;
  font-weight: bold;
}
.icon{
  width: 25px;
  height: 25px;
}
.icon-field{
  margin-top: 10px;
}
.icon-field p{
  padding-left: 15px;
  font-size: 16px;
}
.left-padding {
 margin: 20px;
}
.share{
  margin: 15px;
}
.share textarea{
  width: 100%;
  height: 120px;
  margin-top: 15px;
  margin-bottom: 15px;
  border-radius: 15px;
  background-color: #15202b;
  color: white;
  border: 1px solid white;
  resize: none;
}
button{
  width: 100px;
  color: white;
  background-color: #5419da;
  border-radius: 15px;
  display: block;
  margin: 0 0 0 auto;
}
.text {
 margin-top: 10px;
}
.detail {
 margin-left: 50px;
}
.name {
 font-size: 18px;
 font-weight: bold;
 margin-right: 10px;
}
.message {
 padding: 20px;
 border-bottom: solid 1px white;
 border-left: solid 1px white;
}
.number {
 margin-left: 10px;
 margin-right: 10px;
}
.right{
  width: 80%;
  height: 100vh;
}
.title{
  border-bottom: 1px solid white;
}
</style>