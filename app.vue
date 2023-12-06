<template>
  <div class="container">
    <!-- Login Form -->
    <div class="form">
      <input v-model="email" type="text" placeholder="Email" />
      <input v-model="password" type="password" placeholder="Password" />
      <button @click="onLogin" type="submit">Login</button>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async onLogin() {
      await $fetch("http://localhost:8000/api/login", {
        method: "POST",
        body: {
          email: this.email,
          password: this.password,
        },
      }).then(() => {
        // TODO: set cookie
      });
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}
</style>
