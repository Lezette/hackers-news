<template>
  <div class="">
     <div class="flex justify-between items-center w-full px-10 sm:px-0 sm:w-11/12 mx-auto py-5">
       <nuxt-link to="/" class="flex items-center font-bold">
        <p class="text-5xl font-bold">&#8592;</p>
       <p class="text-xl mt-3">Back to posts</p>
       </nuxt-link>
     </div>
     <div class="p-8 sm:w-11/12 mx-auto bg-gray-800">
         <a
          :href="post.url"
          target="_blank"
          rel="noopener noreferrer"
          class="text-lg md:text-2xl font-bold"
        >
          {{post.title}}
        </a>
        <div class="md:flex-column justify-between items-center w-full md:w-6/12 my-3">
          <div>Written By: {{post.user}}</div>
          <div>Written {{post.time_ago}} </div>
          <div>Post type: {{post.type}} </div>
          <div>Total Points: {{post.points}} </div>
          <div>Total Comments: {{post.comments_count}} </div>
          
        </div>
     </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      post: {}
    }
  },
  async created() {
    try {
      const id = this.$route.params.id;
      const res = await this.$axios.get(`/item/${id}`);
      console.log('res.data', res.data);
      this.post = res.data;
    } catch (err) {
      console.log('err', err);
    }
  },
  head() {
    return {
      title: `Hackers News | ${this.post.title || 'Post'}`,
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