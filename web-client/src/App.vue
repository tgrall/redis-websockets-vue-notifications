<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Notifications from Redis"/>

<div class="d-inline-flex p-4">
   <b-alert id="notification" 
      :show="dismissCountDown"
      dismissible
      @dismissed="dismissCountDown=0"
      @dismiss-count-down="countDownChanged"
    >
    New notification: {{message}}
   </b-alert>
</div>



  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data() {
    return {
      message: "",
      dismissSecs: 20,
      dismissCountDown: 0,      
    }
  },
  created(){
    try {
      const ws = new WebSocket("ws://localhost:3000/");
      ws.onmessage = ({data}) => {
        this.message =  data;
        this.showAlert();
      }
    } catch(err) {
      console.log(err);
    }
  },
  methods: {
    countDownChanged(dismissCountDown) {
      this.dismissCountDown = dismissCountDown
    },
    showAlert() {
      this.dismissCountDown = this.dismissSecs
    }
  },
  components: {
    HelloWorld
  }
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
