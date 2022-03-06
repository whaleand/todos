<template>
  <div class="mt-3 btn-container">
    <div
      class="btn-group"
      role="group"
      aria-label="Basic example"
    >
      <!-- 绑定激活和未激活的类名 -->
      <button
        type="button"
        class="btn"
        :class="active==0?'btn-primary':'btn-secondary'"
        @click="onBnClick(0)"
      >全部</button>
      <button
        type="button"
        class="btn"
        :class="active==1?'btn-primary':'btn-secondary'"
        @click="onBnClick(1)"
      >已完成</button>
      <button
        type="button"
        class="btn"
        :class="active==2?'btn-primary':'btn-secondary'"
        @click="onBnClick(2)"
      >未完成</button>
    </div>

  </div>
</template>

<script>
export default {
  name:'TodoButton',
  // 用自定义事件更新属性值，用固定写法
  emits:['update:active'],
  props:{
    active:{
      type:Number,
      required:true,
      default:0
    }
  },
  methods:{
    onBnClick(index){
      if(this.active==index) return
      this.$emit('update:active',index)
    }
  }
}
</script>

<style>
.btn-container {
  width: 400px;
  text-align: center;
}
</style>