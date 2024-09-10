<script>
import MainHeader from '@/components/MainHeader.vue';
import axios from 'axios';

export default {
  name: 'Login',
  data() {
    return {
      username: '',  // Αλλαγή σε username για να ταιριάζει με το backend
      password: '',
      authenticationFailed: false,
      loading: false
    };
  },
  methods: {
    async handleSubmit() {
      this.loading = true;
      try {
        const response = await axios.post('api/auth/login', {
          username: this.username,
          password: this.password
        });

        localStorage.setItem('token', response.data.token);
        this.$router.push('/home');  // Μετάβαση στην αρχική σελίδα
      } catch (error) {
        this.authenticationFailed = true;
      } finally {
        this.loading = false;
      }
    }
  }
}
</script>

<template>
  <MainHeader>
    <h1 class="fs-3">Login</h1>
    <div class="spinner-border" role="status" v-if="loading">
      <span class="visually-hidden">Loading...</span>
    </div>
    <form v-else @submit.prevent="handleSubmit">
      <div class="mb-2" v-if="authenticationFailed">
        <div class="alert alert-danger" role="alert">
          Authentication failed! Please check your username and password.
        </div>
      </div>
      <div class="mb-2">
        <label for="usernameFormControl" class="form-label mb-1">Username</label>
        <input v-model="username" type="text" class="form-control" id="usernameFormControl" />
      </div>
      <div class="mb-2">
        <label for="passwordFormControl" class="form-label mb-1">Password</label>
        <input v-model="password" type="password" class="form-control" id="passwordFormControl" />
      </div>
      <button type="submit" class="btn btn-primary">
        Login
      </button>
    </form>
  </MainHeader>
</template>
