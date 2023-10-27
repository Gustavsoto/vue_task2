<template>
    <div class = "header" :style="{ 'background-color': headerColor }">
        <img src="@/assets/logo (white).svg" class="logo" />
        <h1 class="siteName" :style="{ 'margin-right' : marginRight}">HelloPG</h1>
        <img v-if="loggedIn" src="@/assets/avatar.png" class="avatar" />
        <h1 v-if="loggedIn" class="fullName">{{ full_name }}</h1>
        <button @click="handleLogin" class="login_button">
            {{ loginStatus ? 'LOGOUT' : 'LOGIN' }}
        </button>
    </div>
</template>
  
<script>
    export default {
        data() {
          return {
            user: {
                name: "Gustavs",
                surname: "Cers",
                code: "IT21024"
            },
            loginStatus: false,
            loggedIn: false,
            headerColor: "grey",
            marginRight: "86%"
            };
        },
        computed: {
            full_name() {
            return this.user.name + ' ' + this.user.surname;
            }
        },
        methods: {
            handleLogin() {
                if (this.loginStatus) {
                    //for login
                    const confirmLogout = confirm('Do you want to log out?');
                    if (confirmLogout) {
                    this.loginStatus = false;
                    this.loggedIn = false;
                    this.headerColor = "grey";
                    this.marginRight = "86%";
                    this.$emit('user-logged-out');
                    }
                } else {
                    //for log out
                    const confirmLogin = confirm('Do you want to log in?');
                    if (confirmLogin) {
                    this.loginStatus = true;
                    this.loggedIn = true;
                    this.marginRight = "75%";
                    this.headerColor = "purple";
                    this.$emit('user-logged-in');
                    }
                }
            }
        }
    };
</script>
  
<style scoped>
.header {
  top: 0;
  left: 0;
  position: fixed;
  width: 100%;
  height: 80px;
  background-color: purple;
  display: flex;
  align-items: center;
}

.logo {
  width: 60px;
  margin-left: 20px;
}

.siteName {
  font-size: 24px;
  border: none;
  border-radius: 8px;
  padding: 5px 10px;
  margin-left: 10px;
  margin-right: 86%;
}

.login_button {
  background-color: rgb(90, 0, 90);
  color: white;
  border: none;
  border-radius: 8px;
  padding: 10px 20px;
  cursor: pointer;
  margin-right: 10px;
}

.fullName {
  font-size: 24px;
  margin-right: 30px;
}

.avatar {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin-right: 50px;
  display: flex;
}
</style>