<template>
  <div>
    <Navbar />
    <h1 class=" text-red-600 p-6">Welcome to the Home Page</h1>
  </div>
</template>

<script>
import Navbar from '../components/Navbar.vue'

export default {
  name: 'Home',
  components: {
    Navbar,
  }
}
</script>
