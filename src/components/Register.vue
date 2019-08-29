<template>
    <div>
      <input type="text" v-model="userInfo.username" placeholder="用户名"><br>
      <input type="password" v-model="userInfo.password" placeholder="密码"><br>
      <input type="text" v-model="userInfo.email" placeholder="邮箱"><br>
      <input type="text" v-model="userInfo.phone" placeholder="手机号"><br>
      <input type="text" v-model="userInfo.question" placeholder="密保问题"><br>
      <input type="text" v-model="userInfo.answer" placeholder="答案"><br>
      <button @click="register">注册</button>
    </div>
</template>

<script>
    export default {
      name: "Register",
      data(){
          return{
            userInfo:{
              username:"",
              password:"",
              email:"",
              phone:"",
              question:"",
              answer:""
            }
          }
      },
      methods:{
        register:function () {
          this.$axios.get('http://localhost:8080/user/register.do?username='+this.userInfo.username+'&password='+this.userInfo.password+
                          '&email='+this.userInfo.email+'&phone='+this.userInfo.phone+'&question='+this.userInfo.question+'&answer='+this.userInfo.answer)
            .then(function (response) {
              console.log(response)
              if (response.data.status === 0){
                alert("注册成功！")
              } else {
                alert("注册失败！")
              }
            })
            .catch(function () {
              alert("注册失败！")
            })
        }
      }
    }
</script>

<style scoped>

</style>
