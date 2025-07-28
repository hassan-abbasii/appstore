<template>
  <div class="flex justify-center items-center bg-gray-50 pt-10 min-h-[90vh]">
    <form class="bg-white p-8 rounded shadow-md w-full max-w-md" @submit.prevent="handleRegister">
      <h2 class="text-2xl font-bold mb-6 text-center" style="color: #003566;">Register</h2>
      <div v-if="successMessage" class="mb-4 text-green-600 text-center">{{ successMessage }}</div>
      <div v-if="errorMessage" class="mb-4 text-red-600 text-center">{{ errorMessage }}</div>
      <div class="mb-4">
        <label class="block text-gray-700 mb-2" for="name">Name</label>
        <input id="name" v-model="name" type="text" required class="w-full px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-orange-400" />
      </div>
      <div class="mb-4">
        <label class="block text-gray-700 mb-2" for="email">Email</label>
        <input id="email" v-model="email" type="email" required class="w-full px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-orange-400" />
      </div>
      <div class="mb-4">
        <label class="block text-gray-700 mb-2" for="password">Password</label>
        <input id="password" v-model="password" type="password" required class="w-full px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-orange-400" />
      </div>
      <div class="mb-6">
        <label class="block text-gray-700 mb-2" for="confirmPassword">Confirm Password</label>
        <input id="confirmPassword" v-model="confirmPassword" type="password" required class="w-full px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-orange-400" />
      </div>
      <button type="submit" class="w-full py-2 rounded text-white font-semibold mb-3" style="background-color: #e7501c;">Register</button>
      <div class="text-left text-sm text-gray-500">
        Already have an account?
        <router-link to="/login" class="font-semibold hover:underline ml-1">Login</router-link>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Register',
  data() {
    return {
      name: '',
      email: '',
      password: '',
      confirmPassword: '',
      errorMessage: '',
      successMessage: ''
    }
  },
  methods: {
    async handleRegister() {
      this.errorMessage = ''
      this.successMessage = ''
      // Frontend validation
      if (!this.name || !this.email || !this.password || !this.confirmPassword) {
        this.errorMessage = 'All fields are required.'
        return
      }
      if (this.password !== this.confirmPassword) {
        this.errorMessage = 'Passwords do not match.'
        return
      }
      if (this.password.length < 6) {
        this.errorMessage = 'Password must be at least 6 characters.'
        return
      }
      try {
        const response = await axios.post('/api/register', {
          name: this.name,
          email: this.email,
          password: this.password,
          password_confirmation: this.confirmPassword
        })
        this.successMessage = response.data.message
        this.errorMessage = ''
        // Optionally clear form
        this.name = ''
        this.email = ''
        this.password = ''
        this.confirmPassword = ''
      } catch (error) {
        if (error.response && error.response.data && error.response.data.message) {
          this.errorMessage = error.response.data.message
        } else {
          this.errorMessage = 'Registration failed.'
        }
        this.successMessage = ''
      }
    }
  }
}
</script>
