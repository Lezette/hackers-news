<template>
  <div class="container my-0 mx-auto min-h-screen text-white">
    <div>
      <h1 class="text-3xl md:6xl text-center py-5">
        YC Haacker News Replica
      </h1>
      <div>
        <Post
          v-for="post in posts"
          :key="post.id"
          :id="post.id"
          :title="post.title"
          :url="post.url"
          :author="post.user"
          :comments_count="post.comments_count"
          :points="post.points"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Post from '../components/Post';
export default {
  components: {
    Post
  },
  data() {
    return {
      posts: []
    }
  },
  async created() {
    try {
      const res = await this.$axios.get('/news');
      this.posts = res.data;
    } catch (err) {
      console.log('err', err);
    }
  },
  head() {
    return {
      title: "Hackers News",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Unofficial Hacker News'
        }
      ]
    }
  },
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>
