<template>
    <div class="box">
      <h1>ABOUT ME</h1>
      <h3>Name: {{ user.name }}</h3>
      <h3>Surname: {{ user.surname }}</h3>
      <h3>Code: {{ user.code }}</h3>
    </div>
  </template>
  <script>
  export default {
    data() {
      return {
        user: {
          name: "Gustavs",
          surname: "Cers",
          code: "IT21024",
        },
      };
    },
  };
  </script>
  <style scoped>
  .box {
    top: 80px;
    left: 400px;
    position: fixed;
    padding-top: 20px;
    padding-left: 30px;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
  }
  </style>