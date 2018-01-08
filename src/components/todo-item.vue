<template>
  <li class="todolist__item">
    {{ todo.task }}
    <span class="todolist__remove" @click="removeTask">X</span>
  </li>
</template>

<script>
  export default {
    props: {
      todo: {
        type: Object,
        default: {
          task: "Default task",
          id: 123
        }
      }
    },
    methods: {
      removeTask: function() {
        this.$emit('remove', this.todo.id);
      }
    }
  }
</script>
