<template>
  <div class="list">
    <MyItem v-for="todoObj in todos" :key="todoObj.id" :todos="todoObj" :checkTodo="checkTodo" :deleteTodo="deleteTodo"/>
  </div>
</template>

<script>
import MyItem from './MyItem.vue'

export default {
  name: 'MyList',
  components: { MyItem },
  props: ['todos','checkTodo','deleteTodo']
}
</script>

<style scoped>
.list {
  border: 1px solid #000;
  border-radius: 3px;
}
</style>