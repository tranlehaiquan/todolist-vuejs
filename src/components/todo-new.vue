<template>
  <div class="todolist__addItem">
    <input v-model="newTask" type="text" class="todolist__input" placeholder="Enter task" @keyup.enter="addTask">
    <button @click="addTask" class="todolist__submit">Add</button>
  </div>
</template>

<script>
  export default {
    props: [],
    data() {
      return {
        newTask: '',
      }
    },
    methods: {
      addTask: function() {
        this.$emit('add', this.newTask);
        this.newTask = '';
      }
    }
  }
</script>
