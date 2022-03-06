<template>
  <div class="todo-cantainer">
    <TodoInput @add='onAddNewTask'></TodoInput>
    <!-- 父传子，用v-bind和props -->
    <TodoList
      :list="tasklist"
      class="mt-2"
    ></TodoList>
    <!-- 通过v-model和v-bind实现父子组件属性同步更新 -->
    <TodoButton v-model:active="activeBtnIndex"></TodoButton>
  </div>
</template>

<script>
// 这里必须./不能@
import TodoList from './components/todo-list/TodoList.vue'
import TodoInput from './components/todo-input/TodoInput.vue'
import TodoButton from './components/todo-button/TodoButton.vue'
export default {
  components: {
    TodoList,
    TodoInput,
    TodoButton
  },
  data() {
    return {
      todoList: [
        { id: 1, task: '周一开会', done: false },
        { id: 2, task: '周二聚餐', done: false },
        { id: 3, task: '周三睡觉', done: true }
      ],
      nestId: 4,
      activeBtnIndex: 0
    }
  },
  methods: {
    onAddNewTask(taskname) {
      this.todoList.push({
        id: this.nestId,
        task: taskname,
        done: false
      })
      this.nestId++
    }
  },
  computed: {
    tasklist() {
      switch (this.activeBtnIndex) {
        case 0:
          return this.todoList
        case 1:
          return this.todoList.filter(x=>x.done==true)
        case 2:
          return this.todoList.filter(x=>x.done!==true)
      }
    }
  }
}
</script>

<style lang="less" scoped>
</style>
