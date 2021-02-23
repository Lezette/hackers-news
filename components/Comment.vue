<template>
  <div>
    <div :class="`p-4 bg-gray-800 my-1 ${level === 0 ? 'mb-3':'mb-0'}`">
      <div class="border border-gray-700 p-4 rounded mx-3">
        <div class="grid grid-cols-2 gap-1 lg:w-3/12 md:w-4/12 w-10/12 text-gray-500 text-2xl">
          <p class="ml-5">{{user}}</p>
          <p class="">{{time_ago}}</p>
        </div>
        <div v-html="content" class="py-4 px-2 text-sm" />
      </div>
      <div v-if="comments.length > 0">
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
  </div>
</template>

<script>
export default {
    name: 'Comment',
    props: ['id', 'level', 'user', 'time_ago', 'content', 'comments'],
}
</script>