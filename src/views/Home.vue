<template>
  <MainHeader/>
  <h3 v-if="user">Hi, {{ user.username }} {{ user.email }}</h3>
  <!--<h3 v-if="!user">You are not logged in</h3>-->
</template>

<script>
import axios from 'axios';
import MainHeader from '@/components/MainHeader.vue'; 

export default {
  name: 'Home',
  data() {
    return {
      user: null
    };
  },
  async created() {
    try {
      const response = await axios.get('api/auth/user', {
        headers: {
          Authorization: 'Bearer ' + localStorage.getItem('token')
        }
      });
      this.user = response.data;
    } catch (error) {
      console.error('User not authenticated', error);
      this.user = null;
    }
  }
};
</script>

<style scoped>
/* Στυλ για το component */
</style>
