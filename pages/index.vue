<template>
  <div class="w-11/12 lg:w-10/12 my-0 mx-auto min-h-screen text-white mb-5">
    <div>
      <h1 class="text-3xl md:6xl text-center py-5">
        YC Haacker News Replica
      </h1>
      <div v-if="err !== ''" class="bg-red-300 py-2 px-5 flex justify-between items-center w-10/12 mx-auto">
        <p class="font-bold">{{err}}</p>
        <p class="text-2xl cursor-pointer" @click="clearError">&times;</p>
      </div>
      <div class="md:grid md:grid-cols-2 gap-5" v-if="posts.length">
        <Post
          v-for="post in posts"
          :key="post.id"
          :id="post.id"
          :title="post.title"
          :url="post.url"
          :author="post.user"
          :comments_count="post.comments_count"
          :points="post.points"
          :time_ago="post.time_ago"
        />
      </div>
      <div v-else class="flex justify-center items-center h-56">
        <Loading />
        <Loading />
      </div>
    </div>
    <div class="flex justify-between w-6/12 md:w-2/12 mx-auto">
        <button class="border border-grey-500 px-5 py-3" :disabled="page === 1" @click="fetch(page = page - 1)">prev</button>
        <button class="border border-grey-500 px-5 py-3" :disabled="page === 10" @click="fetch(page = page + 1)">next</button>
    </div>
  </div>
</template>

<script>
import Post from '../components/Post';
import Loading from '../components/Loading';
export default {
  components: {
    Post,
    Loading
  },
  data() {
    return {
      posts: [],
      page: 1,
      err: '',
    }
  },
  async created() {
    this.fetch();
  },
  methods: {
    async fetch (page = 1) {
      page = page < 1 ? 1 : page > 10 ? 10 : page;
      try {
          const res = await this.$axios.get(`/news?page=${page}`);
          this.posts = res.data;
          this.err = '';
      } catch (err) {
          this.err = `An Error occurred: ${err}`
      }
    },
    clearError() {
      this.err = '';
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