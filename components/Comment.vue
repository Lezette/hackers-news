<template>
  <div>
      <ul class="p-4 ml-2">
          <Child
            :id="id"
            :content="content"
            :comments="comments"
            :level="level"
          />
      </ul>
      <!-- 'id', 'content', 'comments' -->
  </div>
</template>

<script>
import Child from './Child';
export default {
    name: 'Comment',
    props: ['id', 'level', 'user', 'time_ago', 'content', 'comments'],
    components: {
    Child
  },

}
</script>
