<template>
  <li class="">
    <div class="bg-red-300">{{ content }}</div>
    <div class="label">{{ level }}</div>

    
    <!-- <div class="label">Comments</div> -->
    <!-- <div class="label">{{ comments }}</div> -->

    <!-- <ul v-if="comments && comments.length">
      <Child
        :v-for="comment in comments"
        :comment="comment"
      />
    </ul> -->

  </li>
</template>

<script>
export default {
    name: 'Child',
    props: {
        comments: Array,
        content: String,
        level: Number
    }
}
</script>
