<template>
  <div class="list-item">
    <div>
      <input type="checkbox" id="item-tit" :checked="todos.done" @change="handleCheck(todos.id)" />
      <span>{{ todos.title }}</span>
    </div>
    <div class="item-delete" @click="handleDelete(todos.id)">删除</div>
  </div>
</template>

<script>
export default {
  name: 'MyItem',
  data() {
    return {
    }
  },
  props: ['todos', 'checkTodo', 'deleteTodo'],
  methods: {
    handleCheck(id) {
      this.checkTodo(id)
    },
    handleDelete(id) {
      if (confirm('您确认要删除吗？')) { this.deleteTodo(id) }
    }
  },
}
</script>

<style scoped>
.list-item {
  display: flex;
  height: 30px;
  border-bottom: 1px solid #000;
  cursor: pointer;
  padding: 0 3px;
  align-items: center;
  justify-content: space-between;
}
.list-item:hover {
  background-color: #eee;
}
.list-item:last-child {
  border-bottom: 0px;
}
.list-item input {
  margin: 0 5px;
}
.list-item div:last-child {
  display: none;
  padding: 5px;
  text-align: center;
  border-radius: 6px;
  background-color: palevioletred;
  color: #fff;
  font-size: 12px;
}
.list-item:hover div:last-child {
  display: block;
}
</style>