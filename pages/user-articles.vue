<template>
  <div class="container mx-auto px-4 py-8">
    <h2 class="text-3xl font-bold">我的文章</h2>
    <div v-if="articles.length">
      <ul>
        <li v-for="article in articles" :key="article.id" class="border-b py-2">
          <h3 class="text-xl">{{ article.title }}</h3>
          <p>{{ article.summary }}</p>
          <p>{{ article.published_at }}</p>
        </li>
      </ul>
    </div>
    <div v-else>
      <p>暫無文章</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      articles: []
    }
  },
  async mounted() {
    try {
      const token = localStorage.getItem('token')
      const response = await this.$axios.get('/api/user/articles', {
        headers: {
          Authorization: `Bearer ${token}`
        }
      })
      this.articles = response.data.articles
    } catch (error) {
      console.error(error)
      alert('無法加載文章')
    }
  }
}
</script>

<style scoped lang="scss">
.container {
  @apply max-w-7xl mx-auto;
}
</style>
