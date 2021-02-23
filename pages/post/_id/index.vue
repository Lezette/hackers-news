<template>
  <div class="text-white">
     <div class="flex justify-between items-center w-full px-10 sm:px-0 sm:w-11/12 mx-auto py-5">
       <nuxt-link to="/" class="flex items-center font-bold">
        <p class="text-5xl font-bold">&#8592;</p>
       <p class="text-xl mt-3">Back to posts</p>
       </nuxt-link>
     </div>
      <div v-if="err !== ''" class="bg-red-300 py-2 px-5 flex justify-between items-center w-10/12 mx-auto">
      <p class="font-bold">{{err}}</p>
      <p class="text-2xl cursor-pointer" @click="clearError">&times;</p>
    </div>
     <div  v-if="post">
       <div class="p-8 sm:w-11/12 mx-auto bg-gray-800">
          <a
            :href="post.url"
            target="_blank"
            rel="noopener noreferrer"
            class="text-lg md:text-2xl font-bold"
            >
            {{post.title}}
            </a>
            <div class="md:flex justify-between items-center w-full md:w-6/12 my-3">
              <div>Written By: {{post.user}}</div>
              <div>Written {{post.time_ago}} </div>
              <div>Post type: {{post.type}} </div>
              <div>Total Points: {{post.points}} </div>
              <div>Total Comments: {{post.comments_count}} </div>
            </div>
        </div>
        <div class="w-11/12 mx-auto my-4">
          <div class="text-4xl ">Comments</div>
          <Comment
            v-for="comment in comments"
            :key="comment.id"
            :id="comment.id"
            :content="comment.content"
            :level="comment.level"
            :time_ago="comment.time_ago"
            :user="comment.user"
            :comments="comment.comments"
          />
        </div>
     </div>
     <div v-else class="flex justify-center items-center mt-10">
        <Loading />
     </div>
  </div>
</template>

<script>
import Comment from '../../../components/Comment';
import Loading from '../../../components/Loading';
export default {
  components: {
    Comment,
    Loading
  },
  data() {
    return {
      post: null,
      comments: [],
      err: ''
    }
  },
  async created() {
    try {
      const id = this.$route.params.id;
      const res = await this.$axios.get(`/item/${id}`);
      this.post = res.data;
      this.comments = res.data.comments;
    } catch (err) {
      this.err = `An Error occurred: ${err}`
    }
  },
  methods: {
    clearError() {
      this.err = '';
    }
  },
  head() {
    return {
      title: `Hackers News | Post`,
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

</style>