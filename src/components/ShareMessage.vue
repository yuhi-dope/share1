<template>
  <div class="share">
    <p>シェア</p>
    <textarea v-model="share"></textarea>
    <div @click="send">
      <button>シェアする</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data(){
    return{
      share: "",
    };
  },
  methods:{
    send(){
      if(this.share===""){
        alert("シェアする内容を入力してください");
      }else{
        axios
         .post("morning-shelf-03038/api/shares",{
           user_id: this.$store.state.user.id,
           share: this.share,
         })
         .then((response)=>{
           console.log(response);
           alert("シェアしました");
           this.share="";
           this.$router.go({
             path:this.$router.currentRoute.path,
             force:true,
           });
         });
      }
    },
  },
}
</script>

<style scoped>
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
</style>