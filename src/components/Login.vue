<template>
  <div>
    <input type="text" v-model="user.username" placeholder="请输入用户名"><br>
    <input type="password" v-model="user.password" placeholder="请输入密码"><br>
    <button @click="login">登录</button>
  </div>
</template>

<script>
  export default {
    name: "login",
    data(){
      return{
        user:{
          username:"",
          password:""
        }
      }
    },
    methods:{
      login:function () {
        this.$axios.get('http://localhost:8080/user/login.do?username='+this.user.username+'&password='+this.user.password)
          .then(function (response) {
            console.log(response)
            if (response.data.status === 0){
              alert("登录成功！")
            } else {
              alert("注册失败！")
            }

          })
          .catch(function () {
            alert("登录失败!")
          })
      }
    }
  }
</script>

<style scoped>

</style>
