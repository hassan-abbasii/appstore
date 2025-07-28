<template>
  <div class="flex justify-center items-center bg-gray-50 pt-10 min-h-[90vh]">
    <form class="bg-white p-8 rounded shadow-md w-full max-w-md">
      <h2 class="text-2xl font-bold mb-6 text-center" style="color: #003566;">Login</h2>
      <div class="mb-4">
        <label class="block text-gray-700 mb-2" for="email">Email</label>
        <input id="email" v-model="email" type="email" required class="w-full px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-orange-400" />
      </div>
      <div class="mb-6">
        <label class="block text-gray-700 mb-2" for="password">Password</label>
        <input id="password" v-model="password" type="password" required class="w-full px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-orange-400" />
      </div>
      <button type="submit" class="w-full py-2 rounded text-white font-semibold mb-1" style="background-color: #e7501c;">Login</button>
      <div class="flex justify-between">
        <router-link to="/register" class="py-2 rounded text-gray-500 font-semibold hover:underline transition" style="background: none;">Create Account</router-link>
        <a href="#" class="py-2 rounded text-gray-500 font-semibold hover:underline transition" style="background: none;">Forgot Password?</a>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    // Add your login logic here
  }
}
</script>
