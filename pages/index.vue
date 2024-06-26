<template>
  <div class="container mx-auto px-4 py-8">
    <NavbarComponent />
    <section class="mt-8">
      <h2 class="text-xl font-semibold">簡介網站目的與內容</h2>
      <p class="mt-4">TechBlog 是一個分享最新技術文章的平台，我們致力於提供高品質的技術內容，幫助開發者提升技能。</p>
    </section>
    <section class="mt-8">
      <h2 class="text-xl font-semibold">最新文章</h2>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mt-4">
        <div v-for="article in latestArticles" :key="article.id" class="p-4 border rounded">
          <h3 class="font-bold">{{ article.title }}</h3>
          <p class="mt-2">{{ article.summary }}</p>
        </div>
      </div>
      <div class="mt-4">
        <nuxt-link to="/articles" class="text-blue-500 hover:underline">查看更多文章</nuxt-link>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      latestArticles: [
        { id: 1, title: '文章標題 1', summary: '文章簡介 1' },
        { id: 2, title: '文章標題 2', summary: '文章簡介 2' },
        { id: 3, title: '文章標題 3', summary: '文章簡介 3' }
        // 添加更多假文章數據
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
