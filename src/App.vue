<template>
  <nav>
    <div class="left-links">
      <router-link to="/login">LOGIN</router-link> |
      <router-link to="/shop">SHOP</router-link>
    </div>
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #000000;
}

nav a.router-link-exact-active {
  color: #357ebd; 
}

.left-links {
  float: left;
}

body {
  font-family: 'Arial', sans-serif; 
}

button {
  font-family: 'Arial', sans-serif; 
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button.primary {
  background-color: #4a90e2;
  color: #ffffff; 
}

button.primary:hover {
  background-color: #357ebd;
}
</style>