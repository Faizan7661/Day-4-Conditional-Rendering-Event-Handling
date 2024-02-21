<script setup>
import { ref } from 'vue';

const username = ref('');
const password = ref('');
const loggedIn = ref(false);

const login = () => {
  if (username.value === 'faizan' && password.value === 'pwd') {
    loggedIn.value = true;
  } else {
    alert('Invalid username or password');
  }
};

const logout = () => {
  loggedIn.value = false;
  username.value = '';
  password.value = '';
};
</script>

<template>
<div id="container">
    <div v-if="!loggedIn">
      <h2>Login</h2>
      <form @submit.prevent="login">
        <label for="username">Username:</label>
        <input type="text" id="username" v-model="username" required>
        <br>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required>
        <br>
        <button type="submit">Login</button>
      </form>
    </div>
    <div v-else>
      <h2>Welcome, {{ username }}!</h2>
      <button @click="logout">Logout</button>
    </div>
  </div>
</template>

<style scoped>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f0f0f0;
}

#container {
  max-width: 400px;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
}

h2 {
  font-size: 24px;
  color: royalblue;
  margin-bottom: 20px;
  align-items: center;
}

form {
  display: flex;
  flex-direction: column;
}

label {
  font-weight: bold;
}

input {
  padding: 8px;
  margin-bottom: 10px;
  border-radius: 4px;
  border: 1px solid #ccc;
}

button {
  padding: 8px 16px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  align-items: center;
}

button:hover {
  background-color: #0056b3;
}

</style>