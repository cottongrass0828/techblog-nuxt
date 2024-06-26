<template>
  <nav class="flex justify-between items-center py-4">
    <h1 class="text-2xl font-bold">Lisa 的技術文章</h1>
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
</template>
<script>
export default {
  name: 'NavbarComponent',
  computed: {
    isAuthenticated() {
      return !!localStorage.getItem('token')
    }
  },
  methods: {
    logout() {
      localStorage.removeItem('token')
      alert('已登出')
      this.$router.push('/login')
    }
  }
}
</script>

<style scoped lang="scss">
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
