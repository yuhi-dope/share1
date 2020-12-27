<template>
  <div class="flex">
    <div class="left">
      <SideNavi />
    </div>
    <div class="right">
      <div class="title">
        <p>ホーム</p>
      </div>
      <Message :id="id" />
      <div class="comment">
        <div class="comment-title">
          <p>コメント</p>
        </div>
        <div class="message" v-for="(comment, index) in data" :key="index">
          <div class="flex">
             <p class="name">{{comment.comment_user.name}}</p>
          </div>
          <div>
             <p class="text">{{comment.comment.content}}</p>
          </div>
        </div>
        <input v-model="content" type="text" />
        <div @click="send">
          <button>コメント</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SideNavi from "../components/SideNavi";
import Message from "../components/Message";
import axios from "axios";
export default {
  props: ["id"],
  data() {
    return {
      content: "",
      data: "",
    };
  },
  methods:{
    send(){
      axios
       .post("morning-shelf-03038/api/comment",{
         share_id: this.id,
         user_id: this.$store.state.user.id,
         content: this.content,
       })
       .then((response)=>{
         console.log(response);
         this.content="";
         this.$router.go({
           path: this.$router.currentRoute.path,
           force:true,
         });
       });
    },
    comment(){
      axios
        .get("morning-shelf-03038/api/shares" + this.id)
        .then((response)=>{
          console.log(response);
          this.data=response.data.comment;
        });
    },
  },
  created(){
    this.comment();
  },
  components: {
    SideNavi,
    Message
  }
}
</script>

<style scoped>
.flex{
  display: flex;
}
.left{
  width: 20%;
  height: 100vh;
}
.right{
  width: 80%;
  height: 100vh;
}
.title{
  border-bottom: 1px solid white;
}
.title p {
  font-size: 20px;
  font-weight: bold;
}
.comment-title {
  text-align: center;
  padding-top: 10px;
  padding-bottom: 10px;
  border-bottom: 1px solid white;
  border-left: 1px solid white;
}
.message {
 padding: 20px;
 border-bottom: solid 1px white;
 border-left: solid 1px white;
}
.comment input{
  width: 95%;
  height: 25px;
  margin-top: 15px;
  margin-bottom: 15px;
  margin-left: 10px;
  border: 1px solid white;
  border-radius: 5px;
  background-color: #15202b;
  color: white;
}
button{
  width: 100px;
  text-align: center;
  padding: 8px 0 10px;
  color: white;
  background-color: #5419da;
  border-radius: 15px;
  display: block;
  margin: 0 0 0 auto;
}
.text {
  margin-top: 10px;
  font-size: 10px;
}
</style>