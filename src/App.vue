<template>
  <div id="app">
<!--    <router-view name="loginPage"></router-view>
    <div>

  </div>-->
    <router-view name="content"></router-view>
  </div>
</template>

<script>
import SecondClassNavbar from './components/SecondClassNavbar.vue'
import Navigate from "@/components/Navigate";
import Page from "./components/Page"
import Login from "./views/Login"

export default {
  data(){
    return{
      state: false
    }
  },
  components: {
    SecondClassNavbar,Navigate,
    Page,Login
  },

  methods:{
    changeState(){
      this.state=true
      if(localStorage.getItem("user")!==null) {
        localStorage.removeItem("user")
      }
    }
  },
  created() {
    if(localStorage.getItem("user")!==null){
      this.state=false
    }
    localStorage.setItem("state", this.state)
  }
}
</script>

<style>
body{
  margin: 0;
  padding: 0;
}

</style>

