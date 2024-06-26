<template>
  <div class="container mx-auto px-4 py-8">
    <nav class="flex justify-between items-center py-4">
      <h1 class="text-2xl font-bold">TechBlog</h1>
      <ul class="flex space-x-4">
        <li><nuxt-link to="/">首頁</nuxt-link></li>
        <li><nuxt-link to="/articles">文章列表</nuxt-link></li>
        <li><nuxt-link to="/about">關於我們</nuxt-link></li>
        <li><nuxt-link to="/contact">聯絡我們</nuxt-link></li>
        <li v-if="!isAuthenticated"><nuxt-link to="/login">登入</nuxt-link></li>
        <li v-if="isAuthenticated" @click="logout">登出</li>
        <li v-if="isAuthenticated"><nuxt-link to="/user-articles">我的文章</nuxt-link></li>
      </ul>
    </nav>
    <section class="mt-8">
      <h2 class="text-3xl font-bold">聯絡我們</h2>
      <p class="mt-4">如果您有任何問題或建議，請通過以下表單與我們聯絡。</p>
    </section>
    <section class="mt-8">
      <form @submit.prevent="submitForm">
        <div class="mb-4">
          <label for="name" class="block text-gray-700 font-bold mb-2">姓名</label>
          <input
id="name" v-model="form.name" type="text"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            required />
        </div>
        <div class="mb-4">
          <label for="email" class="block text-gray-700 font-bold mb-2">Email</label>
          <input
id="email" v-model="form.email" type="email"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            required />
        </div>
        <div class="mb-4">
          <label for="message" class="block text-gray-700 font-bold mb-2">訊息</label>
          <textarea
id="message" v-model="form.message"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            required></textarea>
        </div>
        <button
type="submit"
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">發送訊息</button>
      </form>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      }
    }
  },
  methods: {
    submitForm() {
      // 處理表單提交邏輯，例如發送請求到後端 API
      console.log('Form submitted:', this.form)
      // 重置表單
      this.form.name = ''
      this.form.email = ''
      this.form.message = ''
      alert('訊息已發送')
    }
  }
}
</script>

<style scoped lang="scss">
.container {
  @apply max-w-7xl mx-auto;
}
nav ul {
  @apply list-none;
}
nav li {
  @apply inline-block;
}
nav a {
  @apply text-gray-700 hover:text-gray-900;
}
</style>
