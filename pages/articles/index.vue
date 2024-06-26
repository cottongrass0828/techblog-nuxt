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
      <h2 class="text-xl font-semibold">文章列表</h2>
      <div class="mt-4">
        <input v-model="searchKeyword" type="text" placeholder="搜索文章" class="border rounded px-4 py-2 w-full" />
        <div class="flex space-x-4 mt-4">
          <input v-model="startDate" type="date" class="border rounded px-4 py-2" />
          <input v-model="endDate" type="date" class="border rounded px-4 py-2" />
          <select v-model="selectedTag" class="border rounded px-4 py-2">
            <option value="">所有標籤</option>
            <option v-for="tag in tags" :key="tag" :value="tag">{{ tag }}</option>
          </select>
        </div>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mt-8">
        <div v-for="article in filteredArticles" :key="article.id" class="p-4 border rounded">
          <h3 class="font-bold">{{ article.title }}</h3>
          <p class="mt-2">{{ article.summary }}</p>
          <p class="mt-2 text-gray-600">{{ article.date }}</p>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchKeyword: '',
      startDate: '',
      endDate: '',
      selectedTag: '',
      articles: [
        { id: 1, title: '文章標題 1', summary: '文章簡介 1', date: '2023-06-01', tags: ['JavaScript', 'Vue'] },
        { id: 2, title: '文章標題 2', summary: '文章簡介 2', date: '2023-06-10', tags: ['CSS', 'TailwindCSS'] },
        { id: 3, title: '文章標題 3', summary: '文章簡介 3', date: '2023-06-15', tags: ['Nuxt.js', 'SSR'] },
        // 添加更多文章數據
      ],
      tags: ['JavaScript', 'Vue', 'CSS', 'TailwindCSS', 'Nuxt.js', 'SSR']
    }
  },
  computed: {
    filteredArticles() {
      return this.articles.filter(article => {
        const matchesKeyword = this.searchKeyword === '' || article.title.includes(this.searchKeyword) || article.summary.includes(this.searchKeyword)
        const matchesTag = this.selectedTag === '' || article.tags.includes(this.selectedTag)
        const matchesStartDate = this.startDate === '' || new Date(article.date) >= new Date(this.startDate)
        const matchesEndDate = this.endDate === '' || new Date(article.date) <= new Date(this.endDate)
        return matchesKeyword && matchesTag && matchesStartDate && matchesEndDate
      })
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
