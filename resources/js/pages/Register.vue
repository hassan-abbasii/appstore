<template>
  <div class="min-h-screen">
    <Navbar />
    <RegisterComponent />
  </div>
</template>

<script>
import Navbar from '../components/Navbar.vue'
import RegisterComponent from '../components/Register.vue'
export default {
  name: 'Register',
  components: { Navbar, RegisterComponent }
}
</script>
