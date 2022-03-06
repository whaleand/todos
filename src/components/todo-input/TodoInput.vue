<template>
  <form class="form-inline" @submit.prevent="onformSubmit">

  <div class="input-group mb-2 mr-sm-2">
    <div class="input-group-prepend">
      <div class="input-group-text">任务</div>
    </div>
    <input type="text" class="form-control" placeholder="请输入任务" style="width:356px" v-model.trim="taskname">
  </div>


  <button type="submit" class="btn btn-primary mb-2">添加新任务</button>
</form>
</template>

<script>
export default {
  name:'TodoInput',
  emits:['add'],
  data(){
    return{
      taskname:''
    }
  },
  methods:{
    // 表单提交函数
    // 子传父，自定义事件
    onformSubmit(){
      if(this.taskname=='')return alert('任务不能为空！')
      // 不为空，就发送(子传父)
      this.$emit('add',this.taskname)
      // 记住清空
      this.taskname=''
    }
  }
}
</script>

<style>

</style>