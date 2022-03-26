<template>
  <div>
    <header>
      <h3>实现一个简单的待办</h3>
      <input type="text" placeholder="请输入你的任务名称，按回车确认" @keyup.enter="add" v-model="title" />
    </header>
  </div>
</template>

<script>
import { nanoid } from 'nanoid'
export default {
  data() {
    return {
      title: ""
    }
  },
  props: [
    'addTodo'
  ],
  methods: {
    add() {
      if (!this.title.trim()) return alert('输入不能为空哦！')
      const todoObj = { id: nanoid(), title: this.title, done: false }
      this.addTodo(todoObj)
      this.title = ''
    }
  },

}
</script>

<style scoped>
header h3 {
  text-align: center;
  margin-bottom: 10px;
}
header input {
  width: 100%;
  border-radius: 5px;
  height: 35px;
  border: 1px solid #000;
  margin-bottom: 10px;
  padding-left: 5px;
  font-size: 12px;
}
</style>