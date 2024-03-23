<template>

  <div class="login">
    <button @click="login" class="primary">LOGIN</button>
  </div>
</template>

<script>
export default {
  name: 'LoginView',
  methods: {
    login() {
      localStorage.setItem('token', 'token246')
      this.$router.push({ name: 'shop' })
    }
  }
}
</script>
