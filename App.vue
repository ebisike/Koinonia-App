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
const StackNavigator = createStackNavigator(
  {
    Home: Login,
    Details: Login,
  },
  {
    initialRouteName: 'Home',
  }
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
  components: { AppNavigator },

  created() {
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
  height:10px
}
</style>
