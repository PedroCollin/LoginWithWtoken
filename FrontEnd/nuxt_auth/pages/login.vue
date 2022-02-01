<template>
  <form @submit.prevent="submit">
    <h1 class="h3 mb-3 fw-normal">Please sign in</h1>

    <input v-model="username" type="text" class="form-control" placeholder="Usuario" required>

    <input v-model="password" type="password" class="form-control" placeholder="Password" required>

    <button class="w-100 btn btn-lg btn-primary" type="submit">Sign in</button>
  </form>
</template>

<script>
export default {
  name: "login",
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    async submit() {
      await fetch('http://127.0.0.1:8000/api/v1/auth/', {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        credentials: 'include',
        body: JSON.stringify({
          username: this.username,
          password: this.password
        })
      });

      await this.$router.push('/');
    }
  }
}
</script>

