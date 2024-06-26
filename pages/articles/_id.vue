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
      <h2 class="text-3xl font-bold">{{ article.title }}</h2>
      <p class="text-gray-600 mt-2">作者: {{ article.author }} | 發佈日期: {{ article.date }}</p>
      <div class="mt-4" v-html="article.content"></div>
    </section>
    <section class="mt-8">
      <h3 class="text-2xl font-semibold">評論區</h3>
      <div class="mt-4">
        <div v-for="comment in comments" :key="comment.id" class="border-b py-2">
          <p class="font-semibold">{{ comment.username }}</p>
          <p>{{ comment.content }}</p>
        </div>
        <div class="mt-4">
          <input v-model="newComment.username" type="text" placeholder="你的名字" class="border rounded px-4 py-2 w-full" />
          <textarea
v-model="newComment.content" placeholder="你的評論"
            class="border rounded px-4 py-2 w-full mt-2"></textarea>
          <button class="mt-2 bg-blue-500 text-white px-4 py-2 rounded" @click="addComment">提交評論</button>
        </div>
      </div>
    </section>
    <section class="mt-8">
      <h3 class="text-2xl font-semibold">相關文章推薦</h3>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mt-4">
        <div v-for="related in relatedArticles" :key="related.id" class="p-4 border rounded">
          <nuxt-link :to="`/articles/${related.id}`">
            <h4 class="font-bold">{{ related.title }}</h4>
            <p class="mt-2">{{ related.summary }}</p>
          </nuxt-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  asyncData({ params }) {
    // 模擬文章數據
    const articles = [
      { id: 1, title: '文章標題 1', author: '作者 1', date: '2023-06-01', content: '<p>文章內容 1</p>', tags: ['JavaScript', 'Vue'], summary: '文章簡介 1' },
      { id: 2, title: '文章標題 2', author: '作者 2', date: '2023-06-10', content: '<p>文章內容 2</p>', tags: ['CSS', 'TailwindCSS'], summary: '文章簡介 2' },
      { id: 3, title: '文章標題 3', author: '作者 3', date: '2023-06-15', content: '<p>文章內容 3</p>', tags: ['Nuxt.js', 'SSR'], summary: '文章簡介 3' }
      // 添加更多文章數據
    ]
    const article = articles.find(a => a.id === parseInt(params.id))

    // 模擬相關文章推薦
    const relatedArticles = articles.filter(a => a.id !== article.id).slice(0, 3)

    // 模擬評論數據
    const comments = [
      { id: 1, username: '用戶 1', content: '評論內容 1' },
      { id: 2, username: '用戶 2', content: '評論內容 2' }
      // 添加更多評論數據
    ]

    return { article, relatedArticles, comments }
  },
  data() {
    return {
      newComment: {
        username: '',
        content: ''
      }
    }
  },
  methods: {
    addComment() {
      if (this.newComment.username && this.newComment.content) {
        this.comments.push({
          id: this.comments.length + 1,
          username: this.newComment.username,
          content: this.newComment.content
        })
        this.newComment.username = ''
        this.newComment.content = ''
      }
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
