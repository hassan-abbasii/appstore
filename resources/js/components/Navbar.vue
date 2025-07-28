<template>
  <nav class="bg-gray-100 text-blue-900 px-4 py-2 flex items-center shadow-md h-[50px] relative">
    <img src="/public/img/store.png" alt="Store Logo" class="h-10 w-10 mr-0 sm:h-12 sm:w-12 sm:mr-0" />
    <h1 class="text-lg sm:text-xl font-bold whitespace-nowrap ml-2">StoreSphere</h1>
    <div :class="[menuOpen ? 'flex flex-col absolute left-0 top-[50px] w-full bg-gray-100 z-10 p-4 shadow-md sm:static sm:flex-row sm:p-0 sm:w-auto sm:bg-transparent sm:shadow-none' : 'hidden sm:flex', 'sm:flex-row sm:items-center sm:space-x-8 ml-4 sm:ml-8']">
      <ul class="flex flex-col sm:flex-row space-y-2 sm:space-y-0 sm:space-x-8 items-center">
        <li class="text-danger"><router-link to="/">Home</router-link></li>
        <li><router-link to="/blog">Blog</router-link></li>
        <li><router-link to="/brands">Brands</router-link></li>
        <li><router-link to="/categories">Categories</router-link></li>
        <li><router-link to="/about">About</router-link></li>
      </ul>
      <router-link v-if="menuOpen && windowWidth < 640" to="/login" class="mt-4 font-semibold px-3 py-1 rounded transition w-full login-btn text-center">Login</router-link>
    </div>
    <div class="flex-1"></div>
    <router-link v-if="windowWidth >= 640" to="/login" class="hidden sm:block font-semibold px-3 py-1 rounded transition ml-2 login-btn text-center">Login</router-link>
    <button @click="toggleMenu" class="ml-auto sm:hidden p-2 focus:outline-none absolute right-4 top-1/2 -translate-y-1/2">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
    </button>
  </nav>
</template>

<style scoped>
.login-btn {
  background-color: #e7501c;
  color: white;
  transition: background 0.2s, opacity 0.2s;
}
.login-btn:hover {
  opacity: 0.8;
}
</style>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      menuOpen: false,
      windowWidth: window.innerWidth
    }
  },
  mounted() {
    window.addEventListener('resize', this.handleResize);
  },
  beforeUnmount() {
    window.removeEventListener('resize', this.handleResize);
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
    handleResize() {
      this.windowWidth = window.innerWidth;
    }
  }
}
</script>
