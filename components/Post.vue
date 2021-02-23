<template>
  <div>
      <article class="bg-gray-800 p-5 my-3 md:flex justify-between items-center rounded">
        <div class="">
          <div class="text-gray-500 text-2xl my-2">{{author}}</div>
            <a
            :href="url"
            target="_blank"
            rel="noopener noreferrer"
            class="text-lg md:text-xl font-bold"
          >
            {{title}}
          </a>
          
          <div class="flex mt-5 text-xs">
            <div class="bg-gray-700 p-2 mx-1">total comments: {{comments_count}}</div>
            <div class="bg-gray-700 p-2 mx-1">points: {{points}}</div>
            <div class="bg-gray-700 p-2 mx-1">Posted {{time_ago}}</div>
          </div>
        </div>
          <nuxt-link :to="'/post/' + id" class="py-2 px-5 border border-gray-700 rounded block  text-center my-3 md:my-0">
            View
          </nuxt-link>
      </article>
  </div>
</template>

<script>
export default {
    name: 'Post',
    props: ['title', 'id', 'url', 'author', 'comments_count', 'points', 'time_ago']
}
</script>

<style>

</style>