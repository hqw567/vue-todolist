<template>
  <div>
    <footer v-show="todos.length">
      <div>
        <!-- <input type="checkbox" :checked="isAll" @change="checkAll" /> -->
        
        <input type="checkbox" v-model="isAll" />
        <span>已完成 {{ doneTotal }} / 全部 {{ todos.length }}</span>
      </div>
      <div @click="clearAll">清除已完成任务</div>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'MyFooter',
  data() {
    return {
      Check: false
    }
  },
  props: ['todos', 'checkAllTodo', 'clearAllTodo'],
  computed: {
    doneTotal() {
      return this.todos.reduce((pre, current) => {
        return pre + (current.done ? 1 : 0)
      }, 0)
    },
    isAll: {
      get() {
        return this.doneTotal === this.todos.length && this.todos.length > 0
      },
      set(value) {
        this.checkAllTodo(value)
      }
    }
  },
  methods: {
    // checkAll(e) {
    //   this.checkAllTodo(e.target.checked)
    // }
    clearAll() {
      this.clearAllTodo()
    }
  }
}
</script>
<style>
footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 10px 0;
  padding: 0 10px;
}
footer input {
  margin-right: 5px;
}
footer div {
  cursor: pointer;
}
footer div:last-child {
  background-color: palevioletred;
  padding: 5px;
  font-size: 12px;
  color: #fff;
  border-radius: 6px;
  cursor: pointer;
}
</style>