<!-- MainHeader.vue -->
<script setup>
</script>

<template>
  <div class="container">
  <div class="main-header">
    <!-- Τίτλος της Σελίδας -->
    <div class="title-container">
    <h1 class="title"></h1>
    <div class="buttons">
      <button class="btn" @click="$router.push('/login')">Login</button>
      <button class="btn" @click="$router.push('/register')">Register</button>
    </div>
    </div>
    <!-- Navbar -->
    <nav class="navbar">
      <ul>
        <li @click="$router.push('/home')"><a href="about-us">Σχετικά με εμάς</a></li>
        <li @click="$router.push('/request')"><a href="request">Συμμετοχή σε αιμοδοσία</a></li>
       <!-- <li><a href="#"</li> -->
      </ul>
    </nav>
  </div>
  </div>
</template>

<style scoped>

.main-header {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0;
  padding: 0;
  width: 100vw;
  box-sizing: border-box;
  background-color: #f4f3e6;
   /* Background για το Header */
}

.title {
  background-image: url('@/assets/title.png'); /* Αντικατάσταση με τη διαδρομή της εικόνας τίτλου */
  background-size: contain; /* Προσαρμογή εικόνας στο χώρο */
  background-repeat: no-repeat; /* Να μην επαναλαμβάνεται */
  background-position: center; /* Κεντράρισμα της εικόνας */
  margin-top: 10px;
  text-align: center;
  height: 100px; /* Προσθήκη ύψους για να εμφανιστεί η εικόνα */
  width: 100%; /* Πλάτος 100% για να καταλάβει όλο το χώρο */
}
.title-container {
  display: flex; /* Flexbox για τον τίτλο και τα κουμπιά */
  align-items: center;
  justify-content: flex-start; /* Κεντράρει τα στοιχεία */
  width: 80%; /* Ορισμός του πλάτους */
  margin-top: 20px;
}
/* Στυλ για τα Κουμπιά */
.buttons {
  display: flex; /* Flexbox για τα κουμπιά */
  gap: 10px; /* Κενό μεταξύ των κουμπιών */
  margin-left: auto; /* Τοποθετεί τα κουμπιά στα δεξιά */
}

.btn {
  background-color: #e67e22; /* Χρώμα φόντου για τα κουμπιά */
  color: #f4f3e6;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #d35400; /* Εφέ hover */
}
/* Στυλ για το Navbar */
.navbar {
  width: 100%;
  background-image: url('@/assets/header.png'); /* Αντικαταστήστε τη διαδρομή με τη διαδρομή της εικόνας σας */
  background-size: cover; /* Να καλύπτει όλο το πλάτος */
  background-position: center;
  padding: 15px 0;
  margin-top: 20px; /* Απόσταση από τον τίτλο */
}

.navbar ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
}

.navbar ul li {
  margin: 0 15px;
}

.navbar ul li a {
  text-decoration: none;
  color: #f4f3e6; /* Χρώμα κειμένου */
  font-size: 18px; /* Μέγεθος γραμματοσειράς */
  padding: 8px 16px;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.navbar ul li a:hover {
  background-color: #ffa175; /* Εφέ κατά την αιώρηση */
}
</style>
