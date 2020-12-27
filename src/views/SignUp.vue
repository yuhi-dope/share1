<template>
  <div>
    <HeaderAuth />
    <div class="card">
      <p>新規登録</p>
      <div class="form">
        <input placeholder="ユーザーネーム" type="text" v-model="name"/>
        <input placeholder="プロフィール" type="text" v-model="profile"/>
        <input placeholder="メールアドレス" type="email" v-model="email"/>
        <input placeholder="パスワード" type="password" v-model="password"/>
        <button @click="auth">新規登録</button>
      </div>
    </div>
  </div>
</template>

<script>
import HeaderAuth from "../components/HeaderAuth";
import axios from "axios";
export default {
  data(){
    return{
      name:"",
      profile:"",
      email:"",
      password:""
    };
  },
  components:{
    HeaderAuth
  },
  methods:{
    auth(){
      axios
       .post("morning-shelf-03038/api/register",{
         name: this.name,
         profile: this.profile,
         email: this.email,
         password: this.password
       })
       .then(response =>{
         console.log(response);
         this.$router.replace("/");
       })
       .catch(error=>{
         alert(error);
       });
    }
  }
};
</script>

<style scoped>
.card{
  background: #ffffff;
  margin: 100px auto;
  width: 370px;
  border-radius: 5px;
  padding: 15px;
}
.card p{
  color: #000;
  font-weight: bold;
  text-align: center;
}
input{
  color:#000;
  border-radius: 10px;
  border: 1px solid black;
  padding: 5px;
  width: 97%;
  margin-top: 10px;
}
.form{
  text-align: center;
}
.form button{
  margin-top: 15px;
}
button{
  width: 90px;
  text-align: center;
  border-radius: 15px;
  padding: 5px 0 7px;
  color: #ffffff;
  background-color: #5419da;
  cursor: pointer;
}
</style>