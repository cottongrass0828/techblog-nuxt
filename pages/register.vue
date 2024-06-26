<template>
  <div class="container mx-auto px-4 py-8">
    <h2 class="text-3xl font-bold">註冊</h2>
    <form @submit.prevent="register">
      <div class="mb-4">
        <label for="username" class="block text-gray-700 font-bold mb-2">用戶名</label>
        <input
id="username" v-model="username" type="text"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          required />
      </div>
      <div class="mb-4">
        <label for="email" class="block text-gray-700 font-bold mb-2">Email</label>
        <input
id="email" v-model="email" type="email"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          required />
      </div>
      <div class="mb-4">
        <label for="password" class="block text-gray-700 font-bold mb-2">密碼</label>
        <input
id="password" v-model="password" type="password"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          required />
      </div>
      <button
type="submit"
        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">註冊</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      email: '',
      password: ''
    }
  },
  methods: {
    register() {
      try {
        // 發送註冊請求到後端 API
        // const response = await this.$axios.post('/api/register', {
        //   username: this.username,
        //   email: this.email,
        //   password: this.password
        // })
        alert('註冊成功')
        this.$router.push('/login')
      } catch (error) {
        alert('註冊失敗')
        console.error(error)
      }
    }
  }
}
</script>

<style scoped lang="scss">
.container {
  @apply max-w-7xl mx-auto;
}
</style>
