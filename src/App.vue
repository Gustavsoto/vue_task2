<script setup>
import HeaderComponent from './components/HeaderComponent.vue';
import NavigationComponent from './components/NavigationComponent.vue';
import HomeComponent from './components/HomeComponent.vue';
import AboutMeComponent from './components/AboutMeComponent.vue';
</script>

<template>
  <div class="flexContainer">
    <div class="header">
      <HeaderComponent @user-logged-in="userLoggedIn" @user-logged-out="userLoggedOut" />
    </div>
    <div class="content">
      <div>
        <NavigationComponent v-if="loggedIn" @show-home="showHome" @show-about-me="showAboutMe" />
      </div>
      <div>
        <AboutMeComponent v-if="showAboutMeComponent" :user="user" />
      </div>
      <div>
        <HomeComponent v-if="showHomeComponent" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {
    HeaderComponent,
    NavigationComponent,
    HomeComponent,
    AboutMeComponent,
  },
  data() {
    return {
      loggedIn: false,
      user: {
        name: "Gustavs",
        surname: "Cers",
        code: "IT21024",
      },
      showHomeComponent: false,
      showAboutMeComponent: false,
    };
  },
  methods: {
    showHome() {
      this.showHomeComponent = true;
      this.showAboutMeComponent = false;
    },
    showAboutMe() {
      this.showHomeComponent = false;
      this.showAboutMeComponent = true;
    },
    userLoggedIn() {
      this.loggedIn = true;
      this.showHomeComponent = true;
    },
    userLoggedOut() {
      this.loggedIn = false;
      this.showHomeComponent = false;
      this.showAboutMeComponent = false;
    },
  },
};
</script>

<style>
  .flexContainer{
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    background-color: aliceblue;
    width: 100%;
    height: 100%;
  }
  .header{
    display: flex;
    justify-content: flex-start;
    background-color: brown;
  }
  .content{
    display: flex;
  }
</style>
