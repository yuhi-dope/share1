<template>
  <div>
    <div class="left-padding">
      <img class="logo" src="../assets/logo.png" />
      <div class="flex icon-field" @click="$router.push('/home')">
        <img class="icon" src="../assets/home.png" />
        <p>ホーム</p>
      </div>
      <div class="flex icon-field" @click="$router.push('/profile')">
        <img class="icon" src="../assets/profile.png" />
        <p>プロフィール</p>
      </div>
      <div class="flex icon-field" @click="$store.dispatch('logout')">
        <img class="icon" src="../assets/logout.png" />
        <p>ログアウト</p>
      </div>
    </div>
    <ShareMessage />
  </div>
</template>

<script>
import ShareMessage from "../components/ShareMessage";
export default {
  components:{
    ShareMessage
  }
}
</script>


<style scoped>
.logo{
  width: 150px;
  cursor: pointer;
}
.flex{
  display: flex;
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
</style>