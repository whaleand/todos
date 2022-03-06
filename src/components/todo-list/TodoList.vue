<template>
  <ul class="list-group">
    <!-- 列表组 -->
    <li
      class="list-group-item d-flex justify-content-between align-items-center"
      v-for="item in list"
      :key="item.id"
    >
      <!-- 复选框 -->
      <div class="custom-control custom-checkbox">
        <input
          type="checkbox"
          class="custom-control-input"
          :id="item.id"
          v-model="item.done"
        >
        <!-- v3这里的v-model可以实现数据双向绑定，修改数据源 -->
        <label
          class="custom-control-label"
          :for="item.id"
          :class="item.done?'delete':''"
        >{{item.task}}</label>
        <!-- 是否done?来判断是否加上delete属性 -->

      </div>
      <!-- 徽标 -->
      <span class="badge badge-success badge-pill" v-if="item.done">完成</span>
      <span class="badge badge-warning badge-pill" v-else>未完成</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    list: {
      default: [],
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.list-group{
  width: 400px;
}
.delete{
  text-decoration: line-through;
  color: gray;
  font-style: italic;
}
</style>
