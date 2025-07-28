<template>
  <div class="min-h-screen">
    <Navbar />
    <LoginComponent />
  </div>
</template>

<script>
import Navbar from '../components/Navbar.vue'
import LoginComponent from '../components/Login.vue'
export default {
  name: 'Login',
  components: { Navbar, LoginComponent }
}
</script>
