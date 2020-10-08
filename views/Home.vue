<template>
  <view class="body" :style="{height: height}">
    <!-- what's on your mind -->
    <view style="" class="on-your-mind">
      <image class="img"
        :source="{
          uri:
            'https://cdn.pixabay.com/photo/2017/06/13/12/53/profile-2398782_1280.png',
        }"
      />
      <text-input class="input" type="text" name="" id="" placeholder="What's on your mind">
    </view>
    <!-- end mind -->
  </view>
</template>

<script>
import NavigationBar from "react-native-navbar";
import {Dimensions} from "react-native";

export default {
  props: {
    navigation: {
      type: Object,
    },
  },

  data() {
      return { 
          height: Math.round(Dimensions.get("window").height)
      }
  },

  created() {
    if (true) {
    //   this.navigation.navigate("LoginPage");
    }
  },
};
</script>

<style scoped>
.img {
    border-radius: 50px;
    width: 15%;
    height: 50px;
}

.input{
    background-color: rgb(82, 79, 79);
    width: 83%;
    border-radius: 50px;
    padding: 2%;
    color: white;
}

.body{
    background-color: rgb(243, 241, 241);
}

.on-your-mind{
    padding: 10;
    display: flex;
    flex-direction:row;
    justify-content: space-between;
    background-color: white;
    border-radius: 10px;
    margin: 10px;
    padding: 20px;
}
</style>