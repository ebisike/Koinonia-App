<template>
  <view>
    <scroll-view>
      <image
        :style="{ width: width, height: height }"
        :source="{
          uri:
            'https://c8.alamy.com/comp/2BPEMM2/portrait-of-a-happy-woman-standing-with-laptop-over-turquoise-background-2BPEMM2.jpg',
        }"
      />
      <view class="con" style="height: 100%; width: 100%">
        <view class="top-bg"></view>
        <view class="sub-bg">
          <text style="color: #fff; font-size: 30px; font-weight: bold"
            >Create Account</text
          >
          <text class style="color: #fff; font-size: 15px"
            >Hi, Welcome to Koinonia. Please fill the form below to get
            started!</text
          >
        </view>
        <view class="bottom-sec">
          <!-- <form> -->
          <view class="sub-con">
            <text-input class="input" v-model="email" placeholder="Email" />
            <text-input
              class="input"
              v-model="username"
              placeholder="Username"
            />
            <text-input
              class="input"
              v-model="password"
              placeholder="Password"
            />
            <text-input
              class="input"
              v-model="confirmPassword"
              placeholder="Confirm Password"
            />
            <CheckBox value="true" />

            <touchable-opacity class="btn" :on-press="signup">
              <text class="btn-text">Register</text>
            </touchable-opacity>

            <view class="flexy">
              <text>Already have an account? </text>
              <touchable-opacity :on-press="goToSignIn">
                <text class="signup">Sign In</text>
              </touchable-opacity>
            </view>
          </view>
          <!-- </form> -->
        </view>
      </view>
    </scroll-view>
  </view>
</template>

<script>
import { Dimensions } from "react-native";
import { CheckBox } from "react-native";
import NavigationBar from "react-native-navbar";
import axios from "axios";

export default {
  props: {
    navigation: {
      type: Object,
    },
  },
  components: { CheckBox, NavigationBar },
  data() {
    return {
      width: Math.round(Dimensions.get("window").width),
      height: Math.round(Dimensions.get("window").height),
      half: Math.round(Dimensions.get("window").height) / 2,
      email: "",
      username: "",
      password: "",
      confirmPassword: "",
    };
  },

  methods: {
    goToSignIn() {
      this.navigation.navigate("LoginPage");
    },

    signup() {
      if (this.confirmPassword1(this.password, this.confirmPassword)) {
        var url = "/api/account/signup";
        axios
          .post(url, {
            email: this.email,
            username: this.username,
            password: this.password,
          })
          .then((res) => {
            axios
              .post("/api/account/signin", { username: this.username, password: this.password })
              .then((res) => {
                this.navigation.navigate("HomePage");
              })
              .catch((err) => alert(err));
          })
          .catch((err) => alert(err));
      } else {
        alert("Password do not match");
      }
    },

    confirmPassword1(pwd, cPwd) {
      return pwd === cPwd;
    },
  },
};
</script>

<style scoped>
.con {
  position: absolute;
}
.top-bg {
  background-color: rgba(0, 0, 0, 0.5);
  height: 40%;
}

.sub-bg {
  background-color: rgba(0, 0, 0, 0.5);
  padding-bottom: 20px;
  padding-left: 20px;
}

.bottom-sec {
  background-color: rgb(255, 255, 255);
  height: 100%;
}

.input {
  background-color: rgb(255, 255, 255);
  padding: 10px;
  margin-right: auto;
  margin-left: auto;
  margin-top: 20px;
  width: 100%;
  border-width: 2px;
  border-color: #1376d3;
  border-radius: 8px;
}

.btn {
  margin-left: auto;
  margin-right: auto;
  margin-top: 15px;
  background-color: #1376d3;
  padding: 10px;
  border-radius: 8px;
  width: 100%;
}

.btn-text {
  text-align: center;
  color: #fff;
  font-size: 20px;
}

.forgot-p {
  width: 100%;
  margin-top: 8px;
  margin-left: auto;
  margin-right: auto;
}

.forgot-text {
  text-align: right;
  color: #1376d3;
}

.sub-con {
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  margin-top: 2%;
}

.flexy {
  display: flex;
  flex-direction: row;
  margin-left: auto;
  margin-right: auto;
  margin-top: 10%;
}

.box {
  width: 50%;
}

.signup {
  color: #1376d3;
  font-weight: bold;
}
</style>