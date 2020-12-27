<template>
 <div>
   <HeaderAuth />
   <div class="card">
     <p>ログイン</p>
     <div class="form">
       <input placeholder="メールアドレス" type="email" v-model="email"/>
       <input placeholder="パスワード" type="password" v-model="password"/>
       <button @click="auth">ログイン</button>
     </div>
   </div>
 </div>
</template>

<script>
import HeaderAuth from "../components/HeaderAuth";
export default {
  components:{
    HeaderAuth
  },
  methods:{
    auth(){
      this.$store.dispatch("login",{
        email: this.email,
        password: this.password
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