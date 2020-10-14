<template>
  <view class="container" style="flex:1">
    <app-navigator class="bx"></app-navigator>
  </view>
</template>

<script>


import {
  createAppContainer,
  createStackNavigator
} from 'vue-native-router';

import Login from './views/Login.vue'
import Register from './views/Register.vue'
import Home from './views/Home.vue'
import axios from "axios"

const StackNavigator = createStackNavigator(
  {
    LoginPage: Login,
    RegisterPage: Register,
    HomePage: Home,
  },
  {
    initialRouteName: 'LoginPage',
  }
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
  components: { AppNavigator },

  created() {
    axios.defaults.baseURL = "http://146dda538d75.ngrok.io"
  },
  mounted() {
    axios.defaults.baseURL = "http://146dda538d75.ngrok.io"
  },
  updated() {
    axios.defaults.baseURL = "http://146dda538d75.ngrok.io"
  }
}
</script>

<style>
.container {
  background-color: white;
  /* align-items: center;
  justify-content: center;
  flex: 1; */
}
.text-color-primary {
  color: blue;
}

.bx {
  height:10px;
  background-color: blue;
}
</style>
