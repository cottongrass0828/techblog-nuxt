<template>
  <div class="container mx-auto px-4 py-8">
    <h2 class="text-3xl font-bold">登入</h2>
    <form @submit.prevent="login">
      <div class="mb-4">
        <label for="email" class="block text-gray-700 font-bold mb-2">Email</label>
        <input id="email" v-model="email" type="email" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" required />
      </div>
      <div class="mb-4">
        <label for="password" class="block text-gray-700 font-bold mb-2">密碼</label>
        <input id="password" v-model="password" type="password" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" required />
      </div>
      <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">登入</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    async login() {
      try {
        // 發送登入請求到後端 API
        const response = await this.$axios.post('/api/login', {
          email: this.email,
          password: this.password
        })
        // 保存 token 到 localStorage
        localStorage.setItem('token', response.data.token)
        alert('登入成功')
        this.$router.push('/')
      } catch (error) {
        alert('登入失敗')
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
