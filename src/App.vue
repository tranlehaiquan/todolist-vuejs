<template>
  <div id="app">
    <div class="todolist">
      <todo-status :todoListNumber="todoList.length"></todo-status>
      <todo-new @add="add"></todo-new>
      <transition-group
        tag="ul"
        class="todolist__items"
        v-if="todoList.length"
        enter-active-class="rubberBand animated"
        leave-active-class="bounceOut animated"
      >
        <li
          is="todo-item"
          v-for="(todo, index) in todoList"
          v-bind="{todo}"
          v-bind:key="todo"
          @remove="remove">
        </li>
      </transition-group>
    </div>
  </div>
</template>

<script>
import todoNew from './components/todo-new.vue';
import todoStatus from './components/todo-status.vue';
import todoItem from './components/todo-item.vue';
export default {
  components: {
    todoItem, todoNew, todoStatus
  },
  data() {
    return {
      todoList: [
        {
          id: 1,
          task: "Learn Vuejs"
        }
      ]
    }
  },
 methods: {
    add: function(newTask) {
      if(!newTask) return;
      this.todoList.push({
        id: new Date().getTime(),
        task: newTask
      });
    },
    remove: function(id) {
      const idIndex = this.todoList.findIndex( (element) => {
        return element.id === id;
      });
      this.todoList.splice(idIndex, 1);
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  background: #61CBFF;
}

.todolist {
  max-width: 500px;
  margin-top: 50px;
  margin-left: auto;
  margin-right: auto;
}
.todolist__addItem {
  margin-bottom: 15px;
  display: flex;
}
.todolist__input {
  height: 35px;
  padding-left: 10px;
  font-size: 16px;
  border: none;
  margin-right: 10px;
  flex: 1;
}
.todolist__submit {
  height: 35px;
  border: none;
  font-size: 16px;
  padding-left: 10px;
  padding-right: 10px;
  background: #0060FF;
  color: white;
  flex: 0 0 100px;
  cursor: pointer;
}
.todolist__items {
  padding: 0;
  margin: 0;
  list-style: none;
}
.todolist__item {
  background: #B0E6FF;
  padding: 8px 10px;
  margin-bottom: 15px;
  border-radius: 4px;
  /* animation: slaceAppear .3s ease-out; */
  position: relative;
}
.todolist__title {
  font-size: 25px;
  margin-bottom: 10px;
  font-family: monospace;
}
.todolist__remove {
  position: absolute;
  right: 0;
  top: 0;
  width: 30px;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #0060ff;
  color: white;
  cursor: pointer;
  font-family: sans-serif;
}

@keyframes slaceAppear {
  0% {
    transform: scale(0);
  }
  100% {
    transform: scale(1);
  }
}
</style>
