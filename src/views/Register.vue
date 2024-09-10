<template>
  <!-- Χρήση του MainHeader component για το layout -->
  <MainHeader></MainHeader>

    <!-- Form handling in Vue -->
    
    <form @submit.prevent="handleSubmit" class="registration-form">
      <div class="form-group row">
        <label for="username" class="col-sm-2 col-form-label">User Name</label>
        <div class="col-sm-4">
          <input
            type="text"
            class="form-control"
            v-model="user_username"
            id="username"
          />
        </div>
      </div>
      <div class="form-group row">
        <label for="email" class="col-sm-2 col-form-label">Email</label>
        <div class="col-sm-4">
          <input
            type="email"
            class="form-control"
            v-model="user_email"
            id="email"
          />
        </div>
      </div>
      <div class="form-group row">
        <label for="password" class="col-sm-2 col-form-label">Password</label>
        <div class="col-sm-4">
          <input
            type="password"
            class="form-control"
            v-model="user_password"
            id="password"
          />
        </div>
      </div>
      <div>
        <input type="submit" class="btn btn-primary" value="Sign Up" />
      </div>
   
    </form>
    <!-- Message Display -->
    <div v-if="msg" class="alert alert-info">{{ msg }}</div>

    <!-- Login Button with Router Link -->
    <button class="btn btn-secondary" @click="goToLogin">Login</button>
</template>

<script>
// Εισαγωγή του MainHeader component στην αρχή
import MainHeader from '@/components/MainHeader.vue'; // Χρήση της @ για να υποδεικνύεται ο φάκελος src
import axios from 'axios';
export default {
  name: 'Register',
  components: {
    MainHeader, // Δήλωση του component μετά την εισαγωγή του
  },
  data() {
    return {
      user_username: '',
      user_email: '',
      user_password: '',
      msg: ''
    };
  },
  methods: {
    async handleSubmit() {
      const responce = await axios.post('register',{
        user_username:this.user_username,
        user_email:this.user_email,
        user_password:this.user_password
      });
      console.log(responce); 
      this.$router.push('/login'); // Κατευθύνει τον χρήστη στη σελίδα του Login
    }
  }
}
</script>

<style scoped>

/* Τα styles παραμένουν όπως είναι */
.registration-form {
  margin-top: 20px;
}

.form-title {
  text-align: center; /* Center title */
  margin-bottom: 20px; /* Space below title */
  color: #333; /* Darker color for contrast */
}

.registration-form .form-group {
  margin-bottom: 15px; /* Spacing between fields */
}

.registration-form label {
  color: #555; /* Lighter label color */
  font-weight: bold; /* Bold labels */
}

.form-control {
  border-radius: 4px; /* Rounded inputs */
}

.btn {
  border-radius: 4px; /* Rounded buttons */
  font-weight: bold; /* Bold button text */
  margin-top: 20px; /* Προσθέτει απόσταση από τα άλλα στοιχεία */
}

.btn-block {
  width: 100%; /* Full-width buttons */
}

.mt-3 {
  margin-top: 20px; /* Top margin utility */
}
</style>
