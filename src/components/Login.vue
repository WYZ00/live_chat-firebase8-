<template>
  <h2>Login</h2>
  <form action="" @submit.prevent="login">
    <input type="email" placeholder="email" v-model="email">
    <input type="password" placeholder="password" v-model="password">
    <div class="error" v-if="error">{{error}}</div>
    <button>Login</button>
  </form>
</template>

<script>
import { ref } from 'vue'
import userLogin from "../composables/userLogin"
export default {
    
    setup(props,context){
        let email = ref('');
        let password = ref('');
        
        let {error,signIn} = userLogin();

        let login=async()=>{
          let res = await signIn(email.value,password.value);
          if(res){
            // console.log(res.user);
            context.emit("enterChatroom")
          }
        }
        return {email,password,login,error}
    }
}
</script>

<style>

</style>