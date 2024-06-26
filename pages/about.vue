<template>
  <div class="container mx-auto px-4 py-8">
    <nav class="flex justify-between items-center py-4">
      <h1 class="text-2xl font-bold">TechBlog</h1>
      <ul class="flex space-x-4">
        <li><nuxt-link to="/">首頁</nuxt-link></li>
        <li><nuxt-link to="/articles">文章列表</nuxt-link></li>
        <li><nuxt-link to="/about">關於我們</nuxt-link></li>
        <li><nuxt-link to="/contact">聯絡我們</nuxt-link></li>
      </ul>
    </nav>
    <section class="mt-8">
      <h2 class="text-3xl font-bold">關於我們</h2>
      <p class="mt-4">我們的團隊致力於提供最新的技術資訊和高品質的技術文章。</p>
    </section>
    <section class="mt-8">
      <h3 class="text-2xl font-semibold">團隊介紹</h3>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mt-4">
        <div v-for="member in teamMembers" :key="member.id" class="p-4 border rounded">
          <h4 class="font-bold">{{ member.name }}</h4>
          <p class="mt-2">{{ member.role }}</p>
          <p class="mt-2">{{ member.description }}</p>
        </div>
      </div>
    </section>
    <section class="mt-8">
      <h3 class="text-2xl font-semibold">聯絡資訊</h3>
      <p class="mt-4">Email: contact@techblog.com</p>
      <p class="mt-2">Phone: 123-456-7890</p>
      <p class="mt-2">Address: 123 Tech Street, Technology City, TE 12345</p>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      teamMembers: [
        { id: 1, name: 'Alice', role: '主編', description: '負責網站內容和編輯。' },
        { id: 2, name: 'Bob', role: '前端開發', description: '負責網站的前端開發和維護。' },
        { id: 3, name: 'Charlie', role: '後端開發', description: '負責網站的後端開發和伺服器管理。' }
        // 添加更多團隊成員
      ]
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
