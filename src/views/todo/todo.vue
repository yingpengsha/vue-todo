<template>
  <section class="real-app">
    <input
      type="text"
      class="add-input"
      autofocus
      placeholder="接下来要做什么"
      @keyup.enter="addTodo()"
      v-model="addInput"
    >
    <Item
      v-for="todo in filteredTodos"
      :todo="todo"
      :key="todo.id"
      @del="deleteTodo"
    />
    <Tabs
      :filter="filter"
      :todos="todos"
      @toggle="toggleFilter"
      @clearAll="clearCompeled"
    />
  </section>
</template>

<script>
import Item from '../../components/item.vue';
import Tabs from '../../components/tabs.vue';

let id = 0;
export default {
  data() {
    return {
      todos: [
        {
          id: 0,
          content: 'This is todo',
          completed: false,
        },
      ],
      filter: 'all',
      addInput: null,
    };
  },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos;
      }
      if (this.filter === 'completed') {
        return this.todos.filter(todo => todo.completed);
      }
      return this.todos.filter(todo => !todo.completed);
    },
  },
  methods: {
    addTodo() {
      this.todos.unshift({
        id: id += 1,
        content: this.addInput,
        completed: false,
      });
      this.addInput = null;
    },
    deleteTodo(deletId) {
      this.todos.splice(
        this.todos.findIndex(todo => todo.id === deletId), 1,
      );
    },
    toggleFilter(state) {
      this.filter = state;
    },
    clearCompeled() {
      this.todos = this.todos.filter(todo => !todo.completed);
    },
  },
  components: {
    Item,
    Tabs,
  },
};
</script>

<style lang="less" scoped>
.real-app{
  width:600px;
  margin:0 auto ;
  box-shadow:0 0 5px #666;
}
.add-input{
  position: relative;
  width: 100%;
  font-size: 24px;
  font-family: inherit;
  font-weight: inherit;
  line-height: 1.4em;
  outline: none;
  color: inherit;
  padding: 6px;
  border: 1px solid #999;
  box-shadow: inset 0 -1px 5px 0 rgba(0, 0, 0, .5);
  box-sizing: border-box;
  padding: 16px 16px 16px 60px;
}
</style>
