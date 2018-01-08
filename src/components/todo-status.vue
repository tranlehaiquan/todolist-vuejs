<template>
  <h2 class="todolist__title">You have {{todoListNumber}} to do!</h2>
</template>

<script>
export default {
  props: {
    todoListNumber: {
      type: Number,
      default: 0
    }
  }
}
</script>
