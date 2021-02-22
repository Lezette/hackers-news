<template>
  <div>
      <article class="bg-gray-800 p-5 my-3">
        <a
          :href="url"
          target="_blank"
          rel="noopener noreferrer"
          class="text-lg md:text-2xl"
        >
          {{title}}
        </a>
        <div class="flex justify-between w-6/12 mt-5">
          <div>author: {{author}}</div>
          <div>total comments: {{comments_count}}</div>
          <div>points: {{points}}</div>
        </div>
      </article>
  </div>
</template>

<script>
export default {
    name: 'Post',
  props: ['title', 'id', 'url', 'author', 'comments_count', 'points']
}
</script>

<style>

</style>