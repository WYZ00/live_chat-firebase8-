<template>
  <div class="container">
    <NavBar></NavBar>
    <NewChatForm></NewChatForm>
  </div>
</template>

<script>
import NewChatForm from '../components/NewChatForm'
import { watch } from 'vue'
import NavBar from '../components/NavBar'
import getUser from '@/composables/getUser'
import {useRouter} from "vue-router"
export default {
  components: {
    NewChatForm, NavBar },
  setup(){
    let {user} =getUser();
    let router = useRouter();
    watch(user,()=>{
      if(!user.value){
        //redirect welcome
        router.push("/");
      }
    })
  }

}
</script>

<style>

</style>